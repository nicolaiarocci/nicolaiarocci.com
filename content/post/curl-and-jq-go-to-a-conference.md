---
date: 2025-11-21T16:57:44+01:00
title: Curl and jq go to a conference 
tags: ["curl", "jq", "speaking", "bash"]
---

I'm presenting at the [WPC 2025 Conference](https://www.wpc.education) on December 3rd in Milan. My session's topic is Feature Flag Management and Dynamic Configurations in C#.

I will use a Web API as an example project, and since I'll be using curl live to query the it, I'll need to pipe responses through [jq](https://jqlang.org) to obtain nicely formatted JSON for the audience. 

The problem with jq is that it crashes on 400s or 500s because the response body is empty in those cases. Error responses are inherent to the demo, and crashes are not the most desirable thing during a presentation. 

I cooked up a quick bash function that enhances curl and jq. It is called cj (curl + jq) and prevents crashes on errors, displays HTTP status codes with color-coded output (green for success, red for errors), and prettifies JSON responses. 

As I fully expect someone in the audience to raise their hand and ask what the hell "cj" is, I'm posting it for reference so I can point them here if needed (Hi there!).

The function looks like this:


```bash
cj() {
    local response http_code body
    
    response=$(curl -s -w "\n%{http_code}" "$@")
    http_code=${response##*$'\n'}
    body=${response%$'\n'*}
    
    if [[ $http_code =~ ^2[0-9][0-9]$ ]]; then
        echo -e "\033[0;32mHTTP Code: $http_code\033[0m"
        echo "$body" | jq 2>/dev/null || echo "$body"
    else
        echo -e "\033[0;31mHTTP Code: $http_code\033[0m"
        echo -e "\033[0;31m$body\033[0m"
    fi
}
```

It currently sits at the bottom of my .zshrc file. I might turn it into a script in the future, but it's probably going to be short-lived, so I'm happy with its current residence.

It's pretty straightforward, but let's break it down line by line.

```bash
cj() {
```
Defines a function named cj (short for "curl with jq"), which will wrap the standard curl command with automatic JSON formatting and colored output.

```bash
local response http_code body
```
Declares three local variables scoped to this function: `response` will store the full curl output, `http_code` will contain the HTTP status code, and `body` will hold the response body.

```bash
response=$(curl -s -w "\n%{http_code}" "$@")
```
Executes curl with the `-s` flag for silent mode (no progress bar), `-w "\n%{http_code}"` to append a newline and the HTTP status code at the end of the output, and `"$@"` to forward all arguments passed to the function. The entire output is captured in the response variable.

```bash
http_code=${response##*$'\n'}
```
Extracts the HTTP status code using Bash parameter expansion. The `##*$'\n'` pattern removes everything up to and including the last newline, leaving only the status code. This is faster than using external commands like tail.

```bash
body=${response%$'\n'*}
```
Extracts the response body using parameter expansion. The `%$'\n'*` pattern removes the last newline and everything after it (the status code), leaving only the body content. This is more efficient than using, say, sed.

```bash
if [[ $http_code =~ ^2[0-9][0-9]$ ]]; then
```
Checks if the HTTP status code matches the pattern for success responses (2xx). The regex `^2[0-9][0-9]$` matches any three-digit number starting with 2.

```bash
echo -e "\033[0;32mHTTP Code: $http_code\033[0m"
```
Prints the HTTP status code in green color. The `-e` flag enables interpretation of backslash escapes, `\033[0;32m` is the ANSI code for green text, and `\033[0m` resets the color back to default.

```bash
echo "$body" | jq 2>/dev/null || echo "$body"
```
This one was fun. Attempts to format the response body as JSON using jq. If jq is not installed or the body isn't valid JSON, stderr is redirected to `/dev/null` and the `||` operator triggers the fallback, which simply prints the raw body.

```bash
else
        echo -e "\033[0;31mHTTP Code: $http_code\033[0m"
```
For non-2xx responses (errors), prints the HTTP status code in red color using the ANSI code `\033[0;31m`.

```bash
echo -e "\033[0;31m$body\033[0m"
```
Prints the error response body also in red color, making errors immediately visible during the demo.

And that is all.

[^1]: I could improve the API to return valid JSON even on errors, but that would be boring. Scripting bash functions on the fly is fun and keeps me on my toes.

[^2]: Two reasons for posting it here. As a note to my future self (I have been known to Google for my own posts), and because I'm betting on someone in the audience to raise their hand and ask what the hell the "cj" is. If that'll be the case, I'll reference them here.
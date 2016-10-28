# Cookies



> So there's two important points here:
>
> * (1) each cookie is only sent back to the same web site as it came from in the first place, and
>
> * (2) the "contents" of the cookie (the data it contains) can only be made up of whatever information the web server already knew anyway.  For example, a web server can't just say "send me a cookie containing your e-mail address" unless that same web server had already sent you that information in the first place.
>
> *<http://rve.org.uk/dumprequest>*

---

## FAQ

### Does every web request send the browser cookies?

*From: [StackOverflow](http://stackoverflow.com/questions/1336126/does-every-web-request-send-the-browser-cookies)*

> Yes, **as long as the URL requested is within the same domain and path defined in the cookie** (and all of the other restrictions -- secure, httponly, not expired, etc) hold, then the cookie will be sent for every request.

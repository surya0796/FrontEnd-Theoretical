#  Async and Defer
    When the browser loads HTML and comes across a <script>...</script> tag, it can’t continue building the DOM. It must execute the script first. That leads to two important issues: Scripts can’t see DOM elements below them, so they can’t add handlers etc. If there’s a bulky script at the top of the page, it “blocks the page”. 

##   DEFER:
    Scripts with defer never block the page. Scripts with defer always execute when the DOM is ready (but before DOMContentLoaded event). The page content shows up immediately. DOMContentLoaded event handler waits for the deferred script. It only triggers when the script is downloaded and executed. Deferred scripts keep their relative order, just like regular scripts.   

##   ASYNC:
     The async attribute means that a script is completely independent: The browser doesn’t block on async scripts (like defer). Other scripts don’t wait for async scripts, and async scripts don’t wait for them. DOMContentLoaded and async scripts don’t wait for each other:   

#   Image Optimization 
```<link rel="preconnect"  href="https://www.img.example.com">``` 
    Informs the browser that your page intends to establish a connection to another origin, and that you'd like the
    process to start as soon as possible.
    Establishing connections often involves significant time in slow networks, particularly when it comes to secure
    connections, as it may involve DNS lookups (Domain name system (DNS) lookups are how end users obtain the websites
    they search for. It is the way DNS services resolve end-user queries and acquire information related to domains.),
    redirects, and several round trips to the final server that handles the user's request.
    Taking care of all this ahead of time can make your application feel much snappier to the user without negatively
    affecting the use of bandwidth.
    But the browser closes preconnet connection if not used within 10 seconds, wasting all of that early connection
    work.
    ```<link href="https://img.pristyncare.com/new_brand%2Felements%2Flogo.svg" rel="preload" as="image">```
    In general, try to use
    ```<link rel="preload">```, as it's a more comprehensive performance tweak, but do keep
    ```<link rel="preconnect">``` in your toolbelt.
    ``` <link rel="dns-prefetch">``` is another
    ```<link>```type related to connections. This handles the DNS lookup only, but it's got wider browser support, so
    it may serve as a nice fallback.
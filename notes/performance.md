# preformance 

- assists
    - 3rd party assists 
    - image sizes and format jbg 
    - mulible images for different sizes 
    - videos 

- Browser hint 
    - prerender :    
        allows you to specify a webpage to be loaded while the user reads the current page. Even though the page is not rendered, the response is guaranteed to be ready when the user navigates from the current page. Only GET requests are included in the prerender cycle and no JavaScript is executed until the page is loaded.
    - prefitch :    
        a resource the user is likely to navigate to you can use the prefetch browser hint to load the page ahead of time. This technique relies on fetching the resource in the background and either the browser cache or even service worker cache to persist the request so the network request is bypassed when the navigation occurs.
    - preconnect :   
        If your document relies on resources coming from external origins or domains the preconnect hint initiates the TCP connection.  The advantage here is you can initiate the connection steps before the first reference in the document. The steps imitated are DNS lookup  TCP handshake  TLS negotiation   
      Just like you add a link reference to the document's header you add a link header to the response's headers. 

    - preload :  
      The preload hint is a declarative fetch, telling the browser to request a resource ahead of time. The advantage is the response is retrieved behind the scenes without blocking the document’s onload event. 



    Browser hints are a great way to optimize your page's load cycles. It does take a little care to understand your page and site's personality to get these setting correct. But even resolving DNS early can provide big wins. Many sites are seeing immediate performance gains by implementing browser hints in their web pages. I know I started DNS prefetching years ago and saw the impact.


- js defer and aysnc  , not render blocking 

- compress text css and js 

- css : load the critical parts first (what the user sees at the start) then the other parts 
- fonts 
    - google fonts : preconect to their domain

    - self hosted fonts :create the font face and only load it if the user dont have it (using gulb to ignore) 
    - font display swap   
        swap gives the font face a zero second block period and an infinite swap period. This means the browser draws text immediately with a fallback if the font face isn't loaded, but swaps the font face in as soon as it loads.
    - preload fonts 
    - use system defult fonts 

- lazy load (images loading = "lazy" and iframe )

- remove unused css files (purge  css)

- remove unsude  js 

- cashing 
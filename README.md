# gdServer

The main project for the OneWeb .net web site. 

This project contains the .csproj and C# code that implements the oneweb /api.  This /api depends upon the ParterAPI.

This project also contains a build process that deploys all the supported applets.


## build commonds

    grunt build - build debug .net server
    grunt compile - build release .net server
    grunt compile-applets - - copies applets/bin to .net /static, moves applet/index.html to .net views - minified 
    grunt build-applets - - copies applets/build to .net /static, moves applet/index.html to .net views - expanded
    

##  considerations:

Support a universal router table that's loaded into all the applets.  The router resolves the URL's applet and path using a table indexed by a product id, and target.  The project id the retail partner.   The target is the screen type; such as mobile, tablet, desktop, and native.


    .net/static/gdRouter/route.json
    routes = [
    {
        product_id: all,
        taget:      all,
        path: "/",
        view: "view/appletGdHome",
    },
    
    {
        product_id: all,
        target:     all,
        path: '/login',
        view:  '/view/appletGdLogin',
    },
    {
        product_id: all,
        target:     all,
        path: '/dashboard',
        view:  '/view/appletGdDashboard',
    },
    {
        product_id: 'necktie',
        target:     all,
        path: '/dashboard',
        view:  '/view/appletNecktieDashboard',
    },
    {
        product_id: 'necktie',
        target:     'small',
        path: '/dashboard',
        view:  '/view/appletNecktieMobileDashbaord',
    }
    ];
    

Runtime support for creating css/html urls based on product, target, language, and theme.  Also support caching that expires on version change.

Each applet has it's own copy of gdClient.  We don't rebuild all applets when we create a new version of the /gdClient code.  
Use CDN for angular, jquery, and fonts caching.

Deploy all applets to .net/static pages.

    cp /:applet/bin .net/static/applet/:applet
    

Deploy applets' index page to .net view.  Add these index views to .csproj.  

    cp /:applet/bin/index.html .net/view/:applet/index.html,

The .net web view router loads the applet's index pages.  For example, the path /view/appletNecktieDashboard/Double-Windsor/video responds with the /view/appletNeckTieDashboard/index.html file.




# Version numbering scheme

    gdClient versions
     1.1.0  - first release cycle (gd release 58)
     1.1.1  - bug release (off cycle)
     1.2.0  - next release cycle (gd release 59)
    appletGdLogin versions
     1.1.0  - first release cycle(gd release 58)
     1.2.0  - first release cycle(gd release 61)
     1.2.1  - emergency bug fix (gd off-cycle release 62)
    appletGdDashboard versions
     1.1.0  - first release cycle(gd release 58)
     1.2.0  - second release cycle(gd release 59)
    appletNecktieDashboard version
     1.1.0   - next year's release

.net solution - C# code that implements the /api.

- the build creates a collection of .net Index.html pages one for each angular app this web site hosts.



grunt build-all  - bower install , build-applets, compile-applets, copy-applets to server

grunt build-applets - cd applet, npm install, bower install, grunt build.  - out /build (mock data)
grunt compile-applets - cd applet, npm install, bower install, grunt build.  - out /bin

grunt build-server  - .net build of /api

grunt deploy-applets - copies applets/bin to .net /static

grunt compile-server - build-server, compile-applets, deploy-applets

- considerations:

build a universal router table that's loaded into all the applets.

    .net/static/gdRouter/route.jsom
    router lookup depends upon /api/route/state - product, target
    
runtime support to build css/html urls using product,target,language,theme

    longlived cache that expires on version change)

manage /static directories.

    put /:applet/bin in .net/static/applet/:applet
    for now, each client has it's own copy of gdClient. KISS
    optimizations puts /gdClient code in a shared version controlled location such as .net/static/gdClient/0.0.0/

manage .net build sources

    put /:applet/bin/index.html in .net/view/:applet/index.html, add this file to .csproj

.net /api must be backward compatible and support all versions of /gdClient code.


we don't update all the applet when we release a new version of the /gdClient code.


Version numbering scheme

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
 1.2.0  - first release cycle(gd release 59)

appletNecktieDashboard version
 1.1.0   - next year release

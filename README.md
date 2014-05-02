.net solution - C# code that implements the /api.

- the build creates a collection of .net Index.html pages one for each angular app this web site hosts.



grunt build-all  - bower install , build-applets, compile-applets, copy-applets to server

grunt build-applets - cd applet, npm install, bower install, grunt build.  - out /build (mock data)
grunt compile-applets - cd applet, npm install, bower install, grunt build.  - out /bin

grunt build-server  - .net build of /api

grunt deploy-applets - copies applets/bin to .net /static

grunt compile-server - build-server, compile-applets, deploy-applets

- considerations:

manage /static directories.
    put /gdClient code in a version controlled location such as .net/static/0.0.0/
    put /:applet/bin in .net/static/applet/:applet
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

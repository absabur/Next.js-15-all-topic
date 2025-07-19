catch all segment.
[...slug], [[...slug]]

privet folders
_lib

underscore in route
"%5F" for underscore

route groups
(route) ignore the route in url

metadata title object
title: {
	default: "show in all the child page that don't have any title",
	template: "%s | show this part after child own title"
}
title: {
 	absolute: "Replace the template title of parent"
}
   
replace in <Link>
forgot the last route, and move to home when go to back

params , searchParams for client and server component
await for server, use() hook for client

layout.js vs template.js
layout doesn't re render while navigate, template re render.

startTransition form 'react'

global-error.js
need html, body full page for this. work only on production mode.

parallel routes
folder start with @
for routing in parallel route we need unmatched route in other route called default.js

intercepted route
(.)route for same level, (..)route for one step up, (..)(..)route for two step up, (...)route for root route. etc

static to dynamic page in ssr
export const dynamic = "force-dynamic" in the top of the page

dynamic to static in ssr
genereteStaticParams() maks ssg static page


---
layout: post
title: ActiveApi - Wrapping a RESTful API in AS3
tags: [programming]
author_name: John
author_uri: http://twitter.com/johnduff
---

<p>

ActiveApi is my AS3 wrapper for a RESTful api, I just came up with
ActiveApi right now so if I'm stepping on someones toes just let me
know.  In <a href="/2008/10/19/wrapping-a-restful-rails-api-in-flex/">my
last post</a> I kind of went over how I came up with these classes so
I'm just going to dive into some code. 

</p>
<p>

To get started you need to define a controller class that extends from
activeapi.base.Controller.  This class should be a singleton, you can do
that however you like.  Controller defines a getter base\_url that just
throws an error so you'll want to override that so it returns your base
url.  This is what you'll get:

</p>
<div style="margin-left: 40px;">

<em>package activeapi.example<br />{<br />    import
activeapi.base.Controller;<br />    <br />    public class
ExampleController extends Controller<br />    {<br />        public
const BASE\_URL:String = "http://localhost:3001/&quot;;<br />       
<br />        private static var ExampleController = new
ExampleController(true);<br />        <br />        public function
TrackerController(only\_one\_allowed:Boolean) {<br />        }<br />   
    <br />        public static function get inst(): ExampleController
{<br />            return \_instance;<br />        }<br /><br />       
public override function get base\_url():String {<br />           
return BASE\_URL;<br />        }<br />    }<br />}</em><br />

</div>
<p>

<br />Controller extends from EventDispatcher so you get all the event
listening and dispatching methods from that.  This is the class that you
will add listeners to for CREATE and DELETE of your objects, like this:

</p>
<div style="margin-left: 40px;">

<em>ExampleController.inst.addEventListener("session&quot;+ActiveEvent.CREATE,
auth);<br /></em>

</div>
<p>

<br />Point to note, I'm prefixing the type of object I am creating to
the event string, this isn't the ideal design but it was the best I
could come up with.

</p>
<p>

Next is defining the class that is going to be doing the RESTful
operations, the Session class in this example.  For now I haven't found
a reason to create a base class to extend from, instead you instantiate
an object that will be used to delegate the work to.  This is what the
basic Session class would look like:

</p>
<div style="margin-left: 40px;">

<em>package activeapi.example<br />{<br />    import
mx.rpc.events.ResultEvent;<br />    import
activeapi.example.base.ActiveEvent;<br />    import
activeapi.example.base.ResourceHandler;<br />    <br />    public class
Session<br />    {<br />        //Static resource handler, passing in
the name of the model and the controller instance.<br />        private
static var resource:ResourceHandler = new
ResourceHandler("session&quot;, ExampleController.inst);<br />       
<br />        public var id:String;<br />        <br />        public
function Session(identifier:String)<br />        {<br />            id =
identifier;<br />        }    <br /><br />        public static function
create(args:Object):void {<br />            //let the resource handler
make the call<br />            resource.create(args,
create\_complete\_callback);<br />        }<br />        // static
create method Session.create<br />        private static function
create\_complete\_callback(event:ResultEvent):void {<br />           
//delegate to the resource handler to handle the basic result and fire
the events.<br />           
resource.handle\_and\_dispatch(ActiveEvent.CREATE,
Session.parse(event.result), event);<br />        }<br />       
<br />        public function destroy():void {<br />           
resource.destroy({id:id}, delete\_complete\_callback);<br />       
}<br />        <br />        private function
delete\_complete\_callback(event:ResultEvent):void {<br />           
resource.handle\_and\_dispatch(ActiveEvent.DELETE, null,
event);<br />        }<br />        <br />        public static function
parse(data:Object):Session {<br />            //return a new session
from the data<br />        }<br />    }<br />}<br /></em>

</div>
<p>

<br />This class has a bit more going on.  First off is the
ResourceHandler, it takes the name of the object type you want to create
and a Controller as it's parameters.  I made mine static so that I could
use it in both my static create method and instance method destroy. 
Under the covers the ResourceHandler sets up some HTTPService objects
pointing to the urls for creating and destroying the session object and
setting op the correct mehod and response type (XML).  These objects
aren't accessible but are used by calling the create and destroy methods
on the ResourceHandler.  In the callback I use another method on the,
handle\_and\_dispatch, to do some basic parsing of the response and then
dispatching the events on the controller.  The second parameter of
handle\_and\_dispatch is an object and is added to the final event that
is dispatched.  The auth method that was added to listen for session
CREATE before might look something like this:<br /><em><br /></em>

</p>
<div style="margin-left: 40px;">

<em>private function auth(event:ActiveEvent):void {</em><br /><em>   
if(Session(event.object).id!=null)</em><br /><em>       
Application.application.currentState =
"logged\_in&quot;</em><br /><em>    else</em><br /><em>       
Alert.show(event.message.toString());</em><br /><em>}</em><br />

</div>
<p>

<br />And that's basically it.  The ExampleController kind of acts like
a central messaging system and the major work is delegated to the
ResourceHandler.  I still need to pull this out from the project I'm
using it for, which shouldn't take long, so if you're interested in the
code let me know in the comments.  I'd also really appreciate some
feedback on the design choices and improvement suggestions.  Personally
I'm still left feeling like there's a better way but trying to figure
something out has been sucking up way too much time.

</p>

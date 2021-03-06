
### YOU MUST HAVE A PUBNUB ACCOUNT TO USE THE API.
### http://www.pubnub.com/account

----------------------------------------------------------
PubNub 3.5 Real-time Cloud Push API - JAVASCRIPT PHONE GAP
----------------------------------------------------------

#### www.pubnub.com - PubNub Real-time Push Service in the Cloud. 
#### http://www.pubnub.com/tutorial/javascript-push-api
####
#### PubNub is a Massively Scalable Real-time Service for Web and Mobile Games.
#### This is a cloud-based service for broadcasting Real-time messages
#### to thousands of web and mobile clients simultaneously.

```
<!-- ============================= -->
<!-- INCLUDE SCRIPT PREFERED STYLE -->
<!-- ============================= -->
<script src=pubnub.min.js></script>
<script>(function(){
    // ----------------------------------
    // PUBNUB
    // ----------------------------------
    var pubnub = PUBNUB({
        publish_key   : 'demo',
        subscribe_key : 'demo',
        ssl           : false,
        origin        : 'pubsub.pubnub.com'
    });

    // ----------------------------------
    // LISTEN FOR MESSAGES
    // ----------------------------------
    pubnub.subscribe({
        channel  : 'test',
        callback : function(message) {
            console.log(JSON.stringify(message));
        },
        error : function() {
            // The internet is gone.
            console.log("Connection Lost");
        }
    });

    // ----------------------------------
    // SEND MESSAGE
    // ----------------------------------
    setInterval( function() {
        pubnub.publish({
            channel  : 'test',
            message  : { example : "Hello World!" },
            callback : function(info) {
                if (info[0])
                    console.log("Successfully Sent Message!");
                else
                    // The internet is gone.
                    console.log("Failed! -> " + info[1]);
            }
        });
    }, 1000 );
})();</script>

<!-- ============================= -->
<!-- SIMPLE EXAMPLE USE PUBNUB API -->
<!-- ============================= -->
<script>
    // ----------------------------------
    // PUBNUB
    // ----------------------------------
    var pubnub = PUBNUB({
        publish_key   : 'demo',
        subscribe_key : 'demo',
        ssl           : false,
        origin        : 'pubsub.pubnub.com'
    });


    // -------------------
    // LISTEN FOR MESSAGES
    // -------------------
    pubnub.subscribe({
        channel  : "hello_world",
        callback : function(message) { alert(message) }
    })

    // ------------
    // SEND MESSAGE
    // ------------
    pubnub.publish({
        channel : "hello_world",
        message : "Hi."
    })

</script>
```

# Event Hopper[https://ac7552.github.io/Event-Hopper/]


## Motivation: 
    I'm a huge fan of Hip Hop music, so the inspiration behind this was to enable fellow Hip Hop heads the opportunity to check out current or upcoming concerts, while they casually search for other things.  


## Languages used: 
   CSS, Javascript

## How to use: 
	Type into the Searchbox and press <Enter> 
	-Your results with markers will pop up
		-These reults are interactive
			-Ratings, and Price Level are available for a select few
	-Current and Upcoming Hip Hop conerts will pop up on the side 
		-Uses long and lat cordinates to find events via Ticket Master
## Code snippet from Event Hopper

	````Javascript 

     //Create markers
     map.setCenter(new google.maps.LatLng( results[0].geometry.location.lat(), results[0].geometry.location.lng() ) )
     for (var i = 0; i < results.length; i++) {
       var marker = new google.maps.Marker({
         map: map,
         icon: results[i].icon,
         title: results[i].name,
         position: {lat: results[i].geometry.location.lat(), lng: results[i].geometry.location.lng()},
         price: results[i].price_level,
         rating: results[i].rating,
       });



   //Get all events from TicketMaster API
   //Filter by Hip Hop concerts  in or after december
   //XMLHttpRequest was used instead of ajax because of CSRF
   function getEvents(lat, long){
     var latlon = lat+","+long
     var xhr = new XMLHttpRequest()
     xhr.open("GET", 'https://app.ticketmaster.com/discovery/v2/events.jsonp?keyword=rap&apikey=5QGCEXAsJowiCI4n1uAwMlCGAcSNAEmG&latlong='+latlon + `&&startDateTime=` +`2016-12-10T00:00:00Z` + `&&classificationName=music` ,true)
     xhr.onreadystatechange = function(){
       if((xhr.readyState==4) && (xhr.status=200)){
         var ob = JSON.parse(xhr.responseText);
        window.Ticket_Master_Events = ob._embedded.events
        $('#outter-ticket').remove()
        ticket_content= `<div id=outter-ticket>`;
        for(i = 0; i < Ticket_Master_Events.length; i++){
           ticket_content += `<div id=ticket> <div id=artistStuff> <img id=artist src=${Ticket_Master_Events[i].images[1].url}  height="42" width="42"></img><br> </div>   <p><b> <a href=${Ticket_Master_Events[i].url} target="_blank">${Ticket_Master_Events[i].name}</a></b></p></div>`
        }
        ticket_content += `</div>`
        $('#center').append(ticket_content)
       }
     };
     xhr.send()
   }

```

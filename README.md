# [Event Hopper](https://ac7552.github.io/Event-Hopper/)


## Motivation: 
    I'm a huge fan of Hip Hop music, so the inspiration behind this was to enable fellow Hip Hop heads the opportunity to check out current or upcoming concerts, while they casually search for other things.  

## Event-Hopper in action
#![New York City Search] (https://github.com/ac7552/Event-Hopper/blob/master/newyork.png)

## Languages used: 
   CSS, Javascript
   
## APIs used 
	Google Maps Places 
	Ticket Master Discovery

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

```

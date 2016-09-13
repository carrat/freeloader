#Formatting CraigsList Data for Front-End

All items should return in a paginated set of unordered list items with the following characteristics:

###Variables stored as item object with representing the number in the output



 var results = [ 
 		item[ i ] {
 		title,
 		location,
 		summary,
 		image,
 		relative_time 
 		}
 		]
 		
 
 

 <ul class="collapsible" data-collapsible="accordion">
 
 		<li>
         <div class="collapsible-header waves-effect" id="item[i]">
         <i class="material-icons blue-text text-darken-1">room</i>
         -- CL Heading --
         </div>
         
         <div class="collapsible-body">   
	         <p> -- CL Body or CL Text -- </p>
	         <a class="btn modal-trigger center-align blue darken-1 more-info 
	         waves-effect" href="#modal1">More Info</a>
         </div>
         
        <div id="modal1" class="modal">
          <div class="modal-content">
            <h4 class="z-depth-2"> -- CL Heading -- </h4>
            <p>
            <img src=" -- CL Image -- " class="modal-img z-depth-2">
            -- CL Body or CL Text -- 
            </p>
            
            <p class="item-address"> -- CL Address -- </p>
            <p class="item-timestamp"> -- CL Timestamp-Relative Time -- </p>
          </div>
        </div>
      </li>
   
  </ul>
  
### Map Data Link
While location data for mapping will not appear in item summary (except address), we will need to store it in an item variable to be accesseed when the item is clicked on.
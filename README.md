select-default-shipping-method
==============================

[WooCommerce] how to select default shipping method

File: woocommerce/includes/class-wc-shipping.php

Look for line "if ( empty( $chosen_method ) || ! isset( $_available_methods[ $chosen_method ] ) ) {"

New code
==============================
if ( empty( $chosen_method ) || ! isset( $_available_methods[ $chosen_method ] ) ) {
						foreach ( $_available_methods as $method_id => $method ) {

							  $string =  $method->label;
							  if(stristr($string, 'UPS Ground') === FALSE) {
							     
							  } else {
							  	 $_cheapest_method 	= $method_id;
							  }
 						/*	 
							if ( $method->cost > $_cheapest_cost || ! is_numeric( $_cheapest_cost ) ) {
								$_cheapest_cost 	= $method->cost;
								$_cheapest_method 	= $method_id;
							}
						*/	
						}
						$chosen_method = $_cheapest_method;
					}

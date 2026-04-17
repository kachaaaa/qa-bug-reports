Bug 2 — Cart reset
Cart items are removed after clicking Back on the Checkout Overview page

Steps to reproduce:
	1.	Login as standard_user
	2.	Add a product to the cart
	3.	Open the cart page
	4.	Click Checkout
	5.	Enter valid data (First Name, Last Name, Zip)
	6.	Click Continue
	7.	On the Checkout Overview page click Back (Cancel)

Actual result:

User is redirected to the products page and the cart becomes empty

Expected result:

Cart items should remain saved after navigating back from the Checkout process

Severity:

High

Priority:

High

---
layout: personal1
title: "Personal - Website Development"
permalink: /personal1
---

<h1 style="text-align:center;margin-top:20px;">Website Development</h1>
<div class="row">
  <hr>
  <h2><a href="#">Freegram.co.uk (Wordpress Blog/Charity Site)</a></h2>
</div>
<div class="row">
	<hr>
	<div class="col-xs-6">
		<img class="enlarge" src="loginFreegram.PNG" style="max-width:90%" max-height="350">
            </div>
	<div class="col-xs-6">
		<h3>WordPress/Social Media Login</h3>
		<p>The site uses WordPress and enables users to signup and login with facebook, google, twitter or youtube quickly and securely in a couple of clicks</p>
	</div>
</div>
<div class="row">
	<hr>
	<div class="col-xs-6">
		<img class="enlarge" src="seperationFreegram.PNG" style="max-width:90%" max-height="350">
	</div>
	<div class="col-xs-6">
		<h3>Blog Categories</h3>
		<p>I Chose to layout the site as a Blog, which would enable users to post their own blogs, projects and news by setting the correct category they could be seperated and easily found</p>
		<p>The main categories include News, Blogs and Projects, this is because the site is primarily supposed to be aimed toward companies with little to no budget/charities who need programming jobs done in exchange for a programmer to gain experience and a reference to add to their portfolio</p>
	</div>
</div>
<div class="row">
	<hr>
	<div class="col-xs-6">
            <img class="enlarge" src="userblogFreegram.PNG" style="max-width:90%" max-height="350">
	</div>
	<div class="col-xs-6">
		<h3>Editing of Plugins</h3>
		<p>The use of plugins make it very easy to knock up a website in a very short time with great functionality, however to get the very best out of wordpress, you need the ability to edit or modify plugins to your liking, i have done this here with limited success as it is a very manual process, by disincluding my own posts into the blogs by users, and likewise with only including my own blogs in the blogs by me section</p>
		<p>Blogs by users will only show other peoples blogs, Blogs by Freegram will only show the blogs posted by me</p>
		<p>I also replicated the behaviour of showing all posts whereby the picture for the post is showing beside the blurb as this was not a default option with the plugin i used.</p>
	</div>
</div>
<div class="row">
	<hr>
	<div class="col-xs-6">
		<img class="enlarge" src="tutislandFreegram.PNG" style="max-width:90%" max-height="350">
	</div>
	<div class="col-xs-6">
		<h3>Tutorial Island</h3>
		<p>This page is a one stop place for many of a budding programmers needs to learn, without having to leave the page they have access to alot of resources from youtube about web development, programming and SEO</p>
	</div>
</div>
<div class="row">
	<hr>
	<div class="col-xs-6">
		<img class="enlarge" src="socialFreegram.PNG" style="max-width:90%" max-height="100">
            </div>
	<div class="col-xs-6">
		<h3>Social Media</h3>
		<p>Using the simple application IFTTT, if this then that, i have made each and every blog, news or project that is posted, also be posted to facebook and twitter.</p>
            </div>
</div>
<div class="row">
	<hr>
	<div class="col-xs-6">
		<img class="enlarge" src="customFreegram.PNG" style="max-width:90%" max-height="350">
	</div>
	<div class="col-xs-6">
		<h3>Custom HTML Pages</h3>
		<p>Of course just because the website uses wordpress predominantly, there is no reason why not to use custom html pages, as such i have created a smoking calculator, and of course this portfolio will be on a custom page on this website</p>
	</div>
</div>
<div class="row">
  <hr>
  <h2><a href="#">SellCards.co.uk (Ecommerce Site)</a></h2>
</div>
<div class="row">
	<hr>
	<div class="col-xs-6">
		<img src="LoginSellCards.PNG" style="max-width:90%" max-height="350">
		<img src="UserDB.PNG" style="max-width:90%">
	</div>
	<div class="col-xs-6">
		<h3>PHP Login/SQL Database</h3>
		<p>Hashing of user passwords using bcrypt</p>
		<p>User can sign up, however no email verification is in place, and log in using this email and the password chosen.</p>
		<p>The website is Secure and uses https:// however it doesnt redirect to this when accessing over http://, this is shown here</p>
		<p>There is an issue i need to fix regarding guest access where it is checking too often whether a user is logged in causing the website to run slowly until the user logs in</p>
	</div>
</div>
<div class="row">
	<hr>
	<div class="col-xs-6">
		<img src="MessageSellCards.PNG" style="max-width:90%" max-height="350">
		<img src="EmailSentSellCards.png" style="max-width:90%" max-height="350"><br>
	</div>
	<div class="col-xs-6">
		<h3>PHP Mail</h3>
		<p>Uses GET to pass the data to the mail php file, although this potentially allows for spam requests so will be changing this to post.</p>
		<p>Below is the code for this as it was short i have included it.</p>
		<code>&lt;?php<br>
			$name=$_GET['name'];<br>
			$email=$_GET['email'];<br>
			$phone=$_GET['phone'];<br>
			$message=$_GET['message'];<br><br>	
			$to = "Email@EMail.com";<br>
			$subject = "Sent from contact form on sellcards.co.uk";<br>
			$txt = $name." ('".$email."/".$phone."') ".$message;<br>
			mail($to,$subject,$txt);<br>
			header( 'Location: https://sellcards.co.uk/index.php' ) ;<br>
			?&gt</code>
	</div>
</div>
<div class="row">
	<hr>
	<div class="col-xs-6">
		<img src="HomePageSellCards.PNG"  style="max-width:90%" max-height="350"><br><br>
		<img src="SearchSellCards.PNG"  style="max-width:90%" max-height="350"><br><br>
		<img src="CardDBSellCards.PNG"  style="max-width:90%" max-height="350">
	</div>
	<div class="col-xs-6">
		<h3>PHP/SQL Search & Sort</h3>
		<p>This function works by reloading the page with new GET parameters which it reads to determine how to order the cards</p>
		<p>A Query is sent to the database and returns the cards based on the above paramaters and the search parameter</p>
		<p>This returns back an array of cards which are displayed in rows on the page to the user, the more results that are returned however the longer it takes to load, other then this it is a quick function</p>
		<h3>CSS Transition</h3>
            <p>Upon hovering over each card, the background will go black, and the card will enlarge and remain highlighted as well as pop out in front of the other cards</p>
		<p>This took alot of trial and error, however the result is very satisfactory.</p>
		<img src="HighlightSellCards.PNG" style="max-width:100%;position:absolute;left:20%;">
	</div>
</div>
        <div class="row">
	<hr>
        <div class="col-xs-6">
		<img src="AccountPageSellCards.PNG"  style="max-width:100%"><br><br>
		<img src="CartsDB.PNG"  style="max-width:100%"><br><br>
		<img src="PaypalCheckoutSellCards.PNG"  style="max-width:100%">
	</div>
	<div class="col-xs-6">
		<h3>PHP/SQL Cart & PayPal</h3>
		<p>The account page includes all the items that the user has added to their cart, able to remove these and is stored in a seperate table in the database, with the fields below to create a connection or foriegn key between tables</p>
		<p>The user's details are also included on this page and in the future i will make this editible by the user</p>
		<p>Once the user has decided to buy the cards in their cart, they can checkout with paypal either by logging in or as a guest, secure and quick.</p>
		<p>The PayPal method i used allows the listing of each item in the transaction, although easier using the built in PayPal buttons, this was not viable for the quantity of different items that my site could potentially handle, just over 15000 if you were wondering, and possibly more depending on any diversity of items decided to be sold. </p>
		<code>$sql="SELECT * FROM cart WHERE userID =".$_SESSION['user'];</code><br>
		<p>This is a simple sql query using php to get relevent information to select everything from the current users cart.</p>
		<code>while ($row = mysqli_fetch_array($query)){<br>
			&emsp;&emsp;&emsp;$query2 = mysqli_query($conn,"SELECT * FROM card WHERE cardID={$row['cardID']}");<br>
			&emsp;&emsp;&emsp;while($row2 = mysqli_fetch_array($query2)){<br>
			&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;${'item'.$i} = $row2['cardName'];<br>
			&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;$i+=1;<br>
			&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;${'item'.$i} = $row2['cardPrice'];<br>
			&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;$i+=1;<br>
			&emsp;&emsp;&emsp;}<br>
			}</code><br>
            <p>This takes the results of the last query and creates another query for each card that was in the cart of the current user returning the card details such as name and price, and adds it to the PayPal itemlist with its requirement to have a name and a price for each item.</p>
	</div>
</div>

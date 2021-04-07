---
layout: personal-highlights
title: "Personal - Website Development"
permalink: /personal1
---

<h1 style="text-align:center;margin-top:20px;">Website Development</h1>
<div class="row">
  <hr>
  <h2>SellCards.co.uk (Ecommerce Site)</h2>
	<p>An Ecommerce website that facilitates selling trading cards</p>
</div>
<div class="row">
	<hr>
	<div class="col-sm-6">
		<img class="enlarge" src="/img/personal/LoginSellCards.PNG" style="max-width:90%;max-height:350px">
		<img class="enlarge" src="/img/personal/UserDB.PNG" style="max-width:90%;max-height:350px">
	</div>
	<div class="col-sm-6">
		<h3>PHP Login/SQL Database</h3>
		<p>Hashing of user passwords using bcrypt.</p>
		<p>User can sign up, however no email verification is in place, and log in using this email and the password chosen.</p>
		<p>The website is secure and uses https:// however it does not redirect to this when accessing over http://, this is shown here.</p>
	</div>
</div>
<div class="row">
	<hr>
	<div class="col-sm-6">
		<img class="enlarge" src="/img/personal/MessageSellCards.PNG" style="max-width:90%;max-height:350px">
		<img class="enlarge" src="/img/personal/EmailSentSellCards.png" style="max-width:90%;max-height:350px"><br>
	</div>
	<div class="col-sm-6">
		<h3>PHP Mail</h3>
		<p>Uses GET to pass the data to the mail php file, although this potentially allows for spam requests accidentally so will be changing this to POST.</p>
		<p>Below is the very simple code for this. </p>
		<code><?php<br>
			$name=$_GET['name'];<br>
			$email=$_GET['email'];<br>
			$phone=$_GET['phone'];<br>
			$message=$_GET['message'];<br><br>	
			$to = "Email@EMail.com";<br>
			$subject = "Sent from contact form on sellcards.co.uk";<br>
			$txt = $name." ('".$email."/".$phone."') ".$message;<br>
			mail($to,$subject,$txt);<br>
			header( 'Location: https://sellcards.co.uk/index.php' ) ;<br>
			?></code>
	</div>
</div>
<div class="row">
	<hr>
	<div class="col-sm-6">
		<img class="enlarge" src="/img/personal/SellcardsHome.PNG"  style="max-width:90%;max-height:350px">
		<img class="enlarge" src="/img/personal/SellcardsSearch.PNG"  style="max-width:90%;max-height:350px">
		<img class="enlarge" src="/img/personal/CardDBSellCards.PNG"  style="max-width:90%;max-height:350px">
	</div>
	<div class="col-sm-6">
		<h3>PHP/SQL Search & Sort</h3>
		<p>This function works by reloading the page with new GET parameters which it reads to determine how to order the cards.</p>
		<p>A query is sent to the database and returns the cards based on the above parameters and the search parameter.</p>
		<p>This returns back an array of cards which are displayed in rows on the page to the user; the more results that are returned however the longer it takes to load, other then this it is a quick function.</p>
	</div>
</div>
<div class="row">
	<hr>
	<div class="col-sm-6">
		<img class="enlarge" src="/img/personal/SellcardsHighlight.PNG" style="max-width:90%" max-height="350">
	</div>
	<div class="col-sm-6">
		<h3>CSS Transition</h3>
		<p>Upon hovering over each card, the background will go black, and the card will enlarge and remain highlighted as well as pop out in front of the other cards.</p>
		<p>This took alot of trial and error, however the result is very satisfactory.</p>
	</div>
</div>
<div class="row">
	<hr>
        <div class="col-sm-6">
		<img class="enlarge" src="/img/personal/SellcardsAccount.PNG"  style="max-width:90%;max-height:350px">
		<img class="enlarge" src="/img/personal/CartsDB.PNG"  style="max-width:90%;max-height:350px">
		<img class="enlarge" src="/img/personal/SellcardsPaypal.PNG"  style="max-width:90%;max-height:350px">
	</div>
	<div class="col-sm-6">
		<h3>PHP/SQL Cart & PayPal</h3>
		<p>The account page includes all the items that the user has added to their cart, able to remove these and is stored in a seperate table in the database, with the fields below to create a connection or foreign key between tables.</p>
		<p>The user's details are also included on this page and in the future I will make this editible by the user.</p>
		<p>Once the user has decided to buy the cards in their cart, they can checkout with PayPal either by logging in or as a guest, secure and quick.</p>
		<p>The PayPal method I used allows the listing of each item in the transaction, although easier using the built in PayPal buttons, this was not viable for the quantity of different items that my site could potentially handle, just over 15,000 if you were wondering, and possibly more depending on any diversity of items that could be sold.</p>
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
		<p>This takes the results of the last query and creates another query for each card that was in the cart of the current user returning the card details such as name and price, adds it to the PayPal itemlist with its requirement to have a name and a price for each item.</p>
	</div>
</div>
<div class="row">
	<hr>
	<h2><a href="https://retrohub.steve-kirby.website">RetroHub.co.uk (Ecommerce Site) </a></h2>
	<p>The link above is a live version of an old backup of this site, as such not all aspects shown below can be tested. (Email:test@test.com, Password:test99)</p>
</div>
<div class="row">
	<hr>
	<div class="col-sm-6">
		<img class="enlarge" src="/img/personal/RetrohubCart.png" style="max-width:90%;max-height:350px">
	</div>
	<div class="col-sm-6">
		<h3>Account/Cart</h3>
		<p>The account page shows the user the products currently in their cart with an ability to remove the item, which can be inspected further by clicking on the item itself.</p>
		<p>The user can checkout using paypal, and has a section where they can view which items are on their wishlist, the wishlist can also contain items that are out of stock.</p>
		<p>The user can subscribe or unsubscribe to marketing emails here as required by GDPR regulations.</p>
	</div>
</div>
<div class="row">
	<hr>
	<div class="col-sm-6">
		<img class="enlarge" src="/img/personal/RetrohubSSL.png" style="max-width:90%;max-height:350px">
		<img class="enlarge" src="/img/personal/RetrohubSignupPage.png" style="max-width:90%;max-height:350px">
		<img class="enlarge" src="/img/personal/RetrohubVisitorTracking.png" style="max-width:90%;max-height:350px">
	</div>
	<div class="col-sm-6">
		<h3>Security and GDPR</h3>
		<p>The Website has an SSL certificate and uses https in all sections of the website where is it is needed, if the user does go to these sections of the website using http, they are redirected to https automatically.</p>
		<p>The user must agree to terms and conditions and privacy policy before they are able to sign up for the website.</p>
		<p>Also the user can subscribe or unsubscribe to marketing emails here, either option will allow the user to sign up.</p>
		<p>The website tracks IP addresses and times for tracking website usage and security, however doesn't use any custom cookies other then the PHP session cookies.</p>
	</div>
</div>
<div class="row">
	<hr>
	<div class="col-sm-6">
		<img class="enlarge" src="/img/personal/RetrohubWishlistOOS.png" style="max-width:90%;max-height:350px">
		<img class="enlarge" src="/img/personal/RetrohubAnotherUser.png" style="max-width:90%;max-height:350px">
	</div>
	<div class="col-sm-6">
		<h3>Preventing Simultanious Sales</h3>
		<p>Due to the unique nature of the items for sale, being that most if not all items are second hand and in varyings states of condition (which the customer can see before they purchase the item). Each item cannot sell more then once.</p>
		<p>These images show a couple of measures to prevent this, being that if the item is in another users cart, they will be told so and given a timeframe before this item can be added to their own cart.</p>
		<p>If an item has already been sold, this item will change to out of stock but is still able to be added to the users wishlist, this is useful for knowing what items are in demand; I would be able to send them an email if they had subscribed to marketing emails.</p>
	</div>
</div>	
<div class="row">
  <hr>
  <h2>Freegram.co.uk (Wordpress Blog/Charity Site)</h2>
	<p>A website that facilitated charity posts and connecting developers with charities.</p>
</div>
<div class="row">
	<hr>
	<div class="col-sm-6">
		<img class="enlarge" src="/img/personal/loginFreegram.PNG" style="max-width:90%;max-height:350px">
            </div>
	<div class="col-sm-6">
		<h3>WordPress/Social Media Login</h3>
		<p>The site uses WordPress and enables users to signup and login with facebook, google, twitter or youtube quickly and securely in a couple of clicks.</p>
	</div>
</div>
<div class="row">
	<hr>
	<div class="col-sm-6">
		<img class="enlarge" src="/img/personal/seperationFreegram.PNG" style="max-width:90%;max-height:350px">
	</div>
	<div class="col-sm-6">
		<h3>Blog Categories</h3>
		<p>I chose to lay the site out as a blog, which would enable users to post their own blogs, projects and news. By setting the correct category, they could be separated and easily found.</p>
		<p>The main categories include News, Blogs and Projects, this is because the site is primarily supposed to be aimed toward companies with little to no budget/charities who need programming jobs done in exchange for a programmer to gain experience and a reference to add to their portfolio.</p>
	</div>
</div>
<div class="row">
	<hr>
	<div class="col-sm-6">
            <img class="enlarge" src="/img/personal/userblogFreegram.PNG" style="max-width:90%;max-height:350px">
	</div>
	<div class="col-sm-6">
		<h3>Editing of Plugins</h3>
		<p>The use of plugins make it very easy to knock up a website in a very short time with great functionality, however to get the very best out of WordPress, you need the ability to edit or modify plugins to your liking, I have done this here with limited success as it is a very manual process, by excluding my own posts into the blogs by users, and likewise with only including my own blogs in the blogs by me section.</p>
		<p>Blogs by users will only show other peoples blogs, Blogs by Freegram will only show the blogs posted by me.</p>
		<p>I also replicated the behaviour of showing all posts whereby the picture for the post is showing beside the blurb as this was not a default option with the plugin I used.</p>
	</div>
</div>
<div class="row">
	<hr>
	<div class="col-sm-6">
		<img class="enlarge" src="/img/personal/tutislandFreegram.PNG" style="max-width:90%;max-height:350px">
	</div>
	<div class="col-sm-6">
		<h3>Tutorial Island</h3>
		<p>This page is a one stop place for many of a budding programmers needs to learn, without having to leave the page they have access to alot of resources from youtube about web development, programming and SEO.</p>
	</div>
</div>
<div class="row">
	<hr>
	<div class="col-sm-6">
		<img class="enlarge" src="/img/personal/socialFreegram.PNG" style="max-width:90%;max-height:100px">
            </div>
	<div class="col-sm-6">
		<h3>Social Media</h3>
		<p>Using the application IFTTT (If This Then That), I have made each and every blog, news or project that is posted, also be posted to facebook and twitter.</p>
            </div>
</div>
<div class="row">
	<hr>
	<div class="col-sm-6">
		<img class="enlarge" src="/img/personal/customFreegram.PNG" style="max-width:90%;max-height:350px">
	</div>
	<div class="col-sm-6">
		<h3>Custom HTML Pages</h3>
		<p>Of course just because the website uses wordpress predominantly, there is no reason why not to use custom html pages, as such I have created a smoking calculator.</p>
	</div>
</div>

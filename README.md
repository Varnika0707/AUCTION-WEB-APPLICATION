# AUCTION-WEB-APPLICATION
"auction web application" using the Django and Vue. Users can create an account on the web app and login / logout. Your custom user model should then also have a profile image, email, and date of birth of the user. The user should be able to edit all these fields in a "profile page". 

Summary of the project:
This folder contains the main, media, user file Where Main files contain the necessary files to make a Django Project. Media file contains the Upload image. User file contains the manage sign-up, login, profile, Ajax and Auction method.
In the User file there is folder called templates where all the html file show such as(auction_list.html, auction.html, base.html, login.html, logout.html, profile.html, signup.html etc). All the files used for display page on the Web Browser.

models.py
import module 
from django.db import models
from django.utils import timezone
from django.contrib.auth.models import AbstractUser
In the user > models.py > There is class CustomUser which inherits the AbstractUser and class Auction which inherits the models. Class CustomUser and Auction have all the fields such as profile_picture, username, email, title, description, starting_price etc.

form.py
import module 
from django import forms
from django.contrib.auth.forms import UserCreationForm
from .models import CustomUser, Auction
In the user>forms.py > class SignupForm inherits the UserCreationFrom and class Meta have a model which inherits the CustomUser and set the fields (inherits CustomUser which is in the models.py). 
class ProfileFrom inherits the ModelForm and class Meta have a model which inherits the CustomUser and set the fields (inherits CustomUser which is in the models.py). 
class AuctionFrom inherits the ModelForm and class Meta have a model which inherits the Auction and set the fields (inherits Auction which is in the models.py).

views.py
import module 
from django.contrib.auth import login, authenticate
from .forms import SignupForm, ProfileForm, AuctionForm
from django.contrib.auth.decorators import login_required
from .models import Auction

Function signup is used for user to Signup the From(SignupForm). If the user is authenticated user can signup the form go to the auction_list page. If user is not authenticated user have to signup the form then login then see the Auction list page.
Function profile_page have ProfileForm. Required login it means if the user is not login/signup. user can not see his/her profile . Only visible the profile_page when user is login his email and password.

Function auction have AuctionForm. This function shows form for Add the Product. If user want to add product user have to login, without login user can’t add a product.

Function auction_list is display the auction list page. When add a product it display the auction_list page.

Ajax call( <script></script> )
Ajax function used in profile.html page for updating the user birth_date, image, username and email. Ajax has a POST method that’s why when you submit and refresh the page then, you can see the updated details.

templates\users
auction_list.html: it contains the all Product.
auction.html: it is a form page for adding Auction product.
base.html:  it is a Navbar from bootstrap and link all the page.
login.html: It’s a login page for user.
logout.html: it is a logout page for current user.
profile.html: it is a profile page for the user.
signup.html: it is a signup form. User have to signup for the first time.

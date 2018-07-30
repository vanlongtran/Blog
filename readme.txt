Ch 5 & 6 Lesson 
Django for Beginners by William S. Vincent
 
-Created a basic blog application following instructions in the chapters.
-Created the Django admin to can create, edit, or delete the content. 
-Used ListView to display entries on home page. Added link to open individual posts.
	#blogs/urls.py
	..
	urlpatterns = [
		path('', views.BlogListView.as_view(), name='home'),
		path('post/<int:pk>/', views.BlogDetailView.as_view(), name='post_detail'),
	]
	..
-The primary key for our post entry which will be represented as an integer <int:pk> are  automatically added as an auto-incrementing primary key to the database models by Django. 
-To add the link in #templates/home.html
	..
	<a href="{% url 'post_detail' post.pk %}">{{ post.title }}</a>
	..
-Used DetailView for to create a detailed individual view of each blog post entry.
-Added static CSS file to improve user experience.


Ch 6
Added forms for individual posts, includes validation in Django Forms abstraction.
-You should add a get_absolute_url() and __str__() method to each model you write. get_absolute_url to assist wih default rerouting.
-Reverse is a very handy utility function Django provides us to reference an object by
its URL template name, in this case post_detail
# reverse('post_detail', args=[str(self.id)])

Add a {% csrf_token %} which Django provides to protect our form from cross-
site scripting attacks

Ch 7
-For user authentication system, Django by default installs the auth app, which provides us with a User objects.
-Used this User object to implement login, logout, and signup in our blog
application.
-Django provides us with a default view for a login page via LoginView. All we need to add are a project-level urlpattern for the auth system, a login template, and update settings.py file.
<!-- templates/registration/login.html -->
{% extends 'base.html' %}
{% block content %}
<h2>Login</h2>
<form method="post">
{% csrf_token %} #prevent a XSS Attack
{{ form.as_p }}  #form’s contents are outputted between paragraph tags
<button type="submit">Login</button>
</form>
{% endblock content %}

Implemented the form class UserCreationForm for new user registration.
-Create a dedicated new app, accounts , for our signup page.
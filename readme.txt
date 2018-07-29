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
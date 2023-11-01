>>> from news.models import *
>>> u1 = User.objects.create_user(username = 'Natalya')
>>> u1
<User: Natalya>
>>> u2 = User.objects.create_user(username = 'Tom')
>>> Author.objects.create(authorUser=u2)
<Author: Author object (2)>
>>> author = Author.objects.get(id=1)
>>> author
<Author: Author object (1)>
>>> 
>>> Post.objects.create(author = author, categoryType = 'NW', title = 'something', text = 'somebigtext')
<Post: Post object (1)>
>>> Post.objects.get(id=1).title
'something'
>>> Post.objects.get(id=1).postCategory.add(Category.object.get.(id=1))
>>> Post.objects.get(id=1).postCategory.add(Category.objects.get(id=1))
>>> Comment.objects.create(commentPost=Post.objects.get(id=1), commentUser=Author.objects.get(id=1), text = 'anytextbyauthor')
>>> Comment.objects.create(commentPost=Post.objects.get(id=1), commentUser=Author.objects.get(id=1).authorUser, text = 'anytextbyauthor')
<Comment: Comment object (1)>
>>> Comment.objects.get(id=1).like()
>>> Comment.objects.get(id=1).rating
1
>>> Comment.objects.get(id=1).dislike()
>>> Comment.objects.get(id=1).dislike()
>>> Comment.objects.get(id=1).dislike()
>>> Comment.objects.get(id=1).rating
-2
>>> Author.objects.get(id=1)
<Author: Author object (1)>
>>> a = Author.objects.get(id=1)
>>> a.update_rating()
Traceback (most recent call last):
  File "<console>", line 1, in <module>
  File "/Users/natalakulikova/PycharmProjects/pythonProject5/project/news/models.py", line 15, in update_rating
    cRat +=commentRat.get('commetRating')
TypeError: unsupported operand type(s) for +=: 'int' and 'NoneType'
>>> a.ratingAuthor
0
>>> a = Author.objects.order_by('-ratingAutor')[:1]
Traceback (most recent call last):
  File "<console>", line 1, in <module>
  File "/Users/natalakulikova/PycharmProjects/pythonProject5/venv/lib/python3.9/site-packages/django/db/models/manager.py", line 87, in manager_method
    return getattr(self.get_queryset(), name)(*args, **kwargs)
  File "/Users/natalakulikova/PycharmProjects/pythonProject5/venv/lib/python3.9/site-packages/django/db/models/query.py", line 1659, in order_by
    obj.query.add_ordering(*field_names)
  File "/Users/natalakulikova/PycharmProjects/pythonProject5/venv/lib/python3.9/site-packages/django/db/models/sql/query.py", line 2221, in add_ordering
    self.names_to_path(item.split(LOOKUP_SEP), self.model._meta)
  File "/Users/natalakulikova/PycharmProjects/pythonProject5/venv/lib/python3.9/site-packages/django/db/models/sql/query.py", line 1724, in names_to_path
    raise FieldError(
django.core.exceptions.FieldError: Cannot resolve keyword 'ratingAutor' into field. Choices are: authorUser, authorUser_id, id, post, ratingAuthor
>>> a = Author.objects.order_by('-ratingAutor')
Traceback (most recent call last):
  File "<console>", line 1, in <module>
  File "/Users/natalakulikova/PycharmProjects/pythonProject5/venv/lib/python3.9/site-packages/django/db/models/manager.py", line 87, in manager_method
    return getattr(self.get_queryset(), name)(*args, **kwargs)
  File "/Users/natalakulikova/PycharmProjects/pythonProject5/venv/lib/python3.9/site-packages/django/db/models/query.py", line 1659, in order_by
    obj.query.add_ordering(*field_names)
  File "/Users/natalakulikova/PycharmProjects/pythonProject5/venv/lib/python3.9/site-packages/django/db/models/sql/query.py", line 2221, in add_ordering
    self.names_to_path(item.split(LOOKUP_SEP), self.model._meta)
  File "/Users/natalakulikova/PycharmProjects/pythonProject5/venv/lib/python3.9/site-packages/django/db/models/sql/query.py", line 1724, in names_to_path
    raise FieldError(
django.core.exceptions.FieldError: Cannot resolve keyword 'ratingAutor' into field. Choices are: authorUser, authorUser_id, id, post, ratingAuthor
>>> for i in a:
... i.ratingAuthor
  File "<console>", line 2
    i.ratingAuthor
    ^
IndentationError: expected an indented block
>>> for i in a:
... ... i.ratingAuthor
  File "<console>", line 2
    ... i.ratingAuthor
    ^
IndentationError: expected an indented block
>>> for i in a:
... i.ratingAuthor
  File "<console>", line 2
    i.ratingAuthor
    ^
IndentationError: expected an indented block
>>> 

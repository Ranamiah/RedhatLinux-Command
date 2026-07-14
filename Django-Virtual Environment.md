# Django-তে Virtual Environment চালুর সম্পূর্ণ Workflow
# Project Folder এ যাও
cd D:\Ostad\Django
# Virtual Environment তৈরি (যদি না থাকে)
python -m venv my_env
# Execution Policy (একবারই)
Set-ExecutionPolicy RemoteSigned

# Virtual Environment চালু
.\my_env\Scripts\Activate.ps1

# Django Install
pip install django

# Project তৈরি
django-admin startproject config
django-admin startproject [project_Name] .
# Project Folder এ যাও
cd config

# Run Server
python manage.py runserver

python manage.py migrate

প্রথমে Django Project Structure

যখন তুমি নিচের কমান্ড দাও:
django-admin startproject myproject
তখন Django এই রকম Structure তৈরি করে:

myproject/
│
├── manage.py
│
├── myproject/
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   ├── asgi.py
│   ├── wsgi.py
│
└── db.sqlite3   (Migration করার পরে)


| File          | মনে রাখার উপায়                              |
| ------------- | -------------------------------------------- |
| `manage.py`   | অফিসের Manager – সব Command চালায়           |
| `settings.py` | Project-এর Brain / Settings                  |
| `urls.py`     | Google Maps / Traffic Police – রাস্তা দেখায় |
| `views.py`    | Chef – Request অনুযায়ী কাজ করে              |
| `models.py`   | Database-এর Table-এর নকশা                    |
| `admin.py`    | Admin Panel-এ Model দেখায়                   |
| `apps.py`     | App-এর পরিচয় ও Configuration                |
| `migrations/` | Database Version History                     |
| `db.sqlite3`  | Database File                                |
| `__init__.py` | Folder-কে Python Package বানায়              |
| `wsgi.py`     | Production Web Server-এর Gateway             |
| `asgi.py`     | Real-time ও Async Application-এর Gateway     |


Django Request Flow (সব ফাইল একসাথে)

Browser
   │
   ▼
manage.py runserver
   │
   ▼
settings.py
(Project Configuration)
   │
   ▼
urls.py
(Route নির্বাচন)
   │
   ▼
views.py
(Logic)
   │
   ▼
models.py
(Database-এর সাথে কাজ)
   │
   ▼
db.sqlite3
(Data Save/Retrieve)
   │
   ▼
views.py
(Response তৈরি)
   │
   ▼
Browser


# ১. manage.py
manage.py
এটা কী?
এটা Django Project-এর Control Panel।
অথবা
Project Manager,
ভাবো তুমি একটি অফিসের ম্যানেজার। সব কর্মচারীকে কাজ দিচ্ছে কে?
👉 Manager ঠিক তেমনি Django-এর সব Command এই ফাইলের মাধ্যমে চলে।
এর কাজ এটার মাধ্যমে তুমি Server চালাও Migration করো App তৈরি করো Superuser বানাও Database Update করো সবকিছু।

কিছু Command
Server চালু:
python manage.py runserver,

Migration তৈরি:
python manage.py makemigrations

Database Update:
python manage.py migrate

App তৈরি:
python manage.py startapp blog
Superuser:
python manage.py createsuperuser
সহজ উদাহরণ
ধরো
একটি স্কুল আছে।
Principal সব কাজ করে না।
Office Manager সবকিছু পরিচালনা করে।
manage.py ঠিক সেই Office Manager।

# ২. settings.py
settings.py
এটা কী?
এটা পুরো Project-এর Brain

অথবা
Configuration File এখানে Django জানে Database কোথায় কোন App Install আছে Static File কোথায় Media কোথায় Time Zone, Language, Security সব।

সবচেয়ে গুরুত্বপূর্ণ অংশ
Installed Apps
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',

নতুন App বানালে
'blog',
এখানে যোগ করতে হবে।

Database
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': BASE_DIR / 'db.sqlite3',
    }
}

এখানে Database Configure হয়।

Time Zone
TIME_ZONE = 'Asia/Dhaka'
Language
LANGUAGE_CODE = 'en-us'
Static
STATIC_URL = 'static/'

বাস্তব উদাহরণ
একটি বাড়ি বানানোর আগে Electricity Water Gas Internet সব Configure করতে হয়। settings.py ঠিক সেই Configuration File।

# ৩. urls.py
urls.py এটা কী?
এটা হচ্ছে Road Map অথবা Traffic Police, Browser Request কোথায় যাবে এটা urls.py ঠিক করে। যদি Browser লেখে localhost:8000/about. urls.py বলে about View-এ যাও।

Example
urlpatterns = [
    path('', views.home),
    path('about/', views.about),

বাস্তব উদাহরণ
তুমি যদি Google Maps-এ Location দাও
Maps রাস্তা দেখায়।
urls.py ঠিক সেটাই করে।

#৪. views.py
এই ফাইল App-এর মধ্যে থাকে। blog/views.py
এটা কী?
এখানে Business Logic থাকে।
Example
def home(request):
    return HttpResponse("Hello")
Browser Request এলো
↓
View কাজ করলো
↓
Response দিল।

বাস্তব উদাহরণ
Restaurant
Customer Order দিল
↓
Chef রান্না করলো
↓
Food দিল
Chef হচ্ছে
views.py

# ৫. models.py
models.py এখানে Database Table তৈরি হয়।

Example
class Student(models.Model):
    name = models.CharField(max_length=100)
এটাই Database Table।

বাস্তব উদাহরণ
Excel Sheet- Name, Age, Phone এই Column গুলো Model।

#৬. admin.py
Admin Panel-এ কোন Model দেখাবে এখানে লেখা হয়।

Example
admin.site.register(Student)
এখন Admin Panel-এ Student দেখা যাবে।

#৭. apps.py
প্রতিটি App-এর Configuration।
Example
class BlogConfig(AppConfig):
Django App Load হওয়ার সময় এটা ব্যবহার করে।

#৮. migrations/
migrations/
এখানে Database History থাকে।
Example
0001_initial.py
মানে
প্রথম Database Version।
বাস্তব উদাহরণ
Software Update
Version 1
Version 2
Version 3

#৯. db.sqlite3
db.sqlite3
এটা Database File।
SQLite Database।
এখানে Users, Products, Orders সব Data থাকে। 
বাস্তব উদাহরণ
Excel File যেখানে Data Save হয়।

#১০. init.py
এটা Python-কে বলে এই Folder একটা Package।
সাধারণত এতে কিছু লিখতে হয় না।

#১১. wsgi.py
অনেকেই এটা বোঝে না।
WSGI =Web Server Gateway Interface
এটা Production Server-এর জন্য। যখন Website Internet-এ Publish করবে তখন Nginx, Apache, Gunicorn এই File ব্যবহার করে।

Flow

User-> Nginx -> Gunicorn -> wsgi.py -> Django

বাস্তব উদাহরণ
Security Guard

Visitor এসেছে -> Guard ভিতরে পাঠালো

#১২. asgi.py
ASGI = Asynchronous Server Gateway Interface এটা নতুন Version।

WebSocket, Chat App, Notification, Live Update, Online Game এসবের জন্য।

Example
ChatGPT
Facebook Messenger
WhatsApp Web
WebSocket ব্যবহার করে।

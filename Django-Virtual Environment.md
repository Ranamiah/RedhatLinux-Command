Django-তে Virtual Environment চালুর সম্পূর্ণ Workflow
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

# Project Folder এ যাও
cd config

# Run Server
python manage.py runserver

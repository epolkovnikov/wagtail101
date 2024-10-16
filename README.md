# wagtail101
Materials for Wagtail basics; Python meetup presentation

## What is Wagtail?

They say it is the leading open-source Python Content Management System (CMS).

I'd say yes, it is a great "here is your box of parts, go assemble a CMS yourself".

If you expect install and run, - no it is not the case.

Read [The Zen of Wagtail](https://docs.wagtail.org/en/stable/getting_started/the_zen_of_wagtail.html) to get it from the authors.

## Why Wagtail?

It is free and Open Source.

Now answer these questions (at least):

Are you building a blog web app with Django and it feels like rewriting a WordPress?

Do uou want your users to be completely isolated from the design part of it?

Have you already touched Django and want a boost with pre-built blocks?

Do you have a feature creep and have to integrate something unusual, or have it more like a Web app?

Or do you have to give access to your data via an API along the pages?

Do you want to get your hands dirty with code?

Is your Python skill is way better than your PHP?

If you answer 'yes' - probably Wagtail is for you :-)

## How Wagtail sites look like?
[A really simple blog / instructionables list](https://www.csanim.com/) | [A personal site](https://www.mahnamahna.net/) | [An event/festival](https://www.jazzfestival.nz/) | 
[A University site](https://www.utas.edu.au/) | [A big org site](https://www.jpl.nasa.gov/)

## Install

Once you are at [Wagtail CMS official website](https://wagtail.org/), don't do 'pip install wagtail' right away. Instead

1. Check what you've got on your system
   
2. Check [the compatibility table](https://docs.wagtail.org/en/stable/releases/upgrading.html#compatible-django-python-versions)

   For example, a standar install, with not much trickery:
   
   On a Rocky 8.10 image with its normal set of repos, after upgrade to Python 3.x, you get
   
   python==3.6, sqlite 3.26, wagtail 2.15.6 - quite old

   Note: While upgrade of Python is possible there wagtail 6.2 requires sqlite 3.27. Rocky 8 system has sqlite 3.26. Only available install is from source. And then requires rebuild of Python. So...

   On Rocky 9:

   python 3.11, sqlite-libs 3.34, wagtail 6.2.1 - somewhat better, yet, the choice is limited by the sqlite.
   
3. Pull instructions and docs for the right version!

   In our case with our Rocky9 - [https://docs.wagtail.org/en/v6.2.1/](https://docs.wagtail.org/en/v6.2.1/)

4. Install Wagtail dependencies (you may already have them, or Wagtail 6.2.2 is resolving them on its own)

```
sudo dnf install -y python3-devel
sudo dnf install -y libjpeg-turbo-devel
```

If you don't have them, you may see the following error on wgatail install on a vanilla Rocky9 image:

```
$ pip3 install wagtail
  The headers or library files could not be found for jpeg,
  a required dependency when compiling Pillow from source.
    
  Please see the install instructions at:
     https://pillow.readthedocs.io/en/latest/installation.html
```

5. Install Wagtail in the virtual environment:
   
5.1. Create and activate the virtual environment (from your home dir, or whatever dev dir):

```
python3 -m venv wt00
source ./wt00/bin/activate # you can change the wt00 to match _your_ application
cd wt00
```

5.2. Install Wagtail (finally :-))

```
pip3 install wagtail
```
Example of a successful result:
```
Successfully installed Django-4.2.16 Pillow-10.4.0 Willow-1.8.0 anyascii-0.3.2 asgiref-3.8.1 beautifulsoup4-4.12.3 certifi-2024.8.30 charset-normalizer-3.3.2 defusedxml-0.7.1 django-filter-24.3 django-modelcluster-6.3 django-permissionedforms-0.1 django-taggit-5.0.1 django-treebeard-4.7.1 djangorestframework-3.15.2 draftjs-exporter-5.0.0 et-xmlfile-1.1.0 filetype-1.2.0 idna-3.10 l18n-2021.3 laces-0.1.1 openpyxl-3.1.5 pillow-heif-0.18.0 pytz-2024.2 requests-2.32.3 six-1.16.0 soupsieve-2.6 sqlparse-0.5.1 telepath-0.3.1 typing-extensions-4.12.2 urllib3-2.2.3 wagtail-6.2.1
WARNING: You are using pip version 21.2.3; however, version 24.2 is available.
You should consider upgrading via the '/home/rocky9/wt00/bin/python3 -m pip install --upgrade pip' command.
```
Note: "WARNING: You are using pip version ..." is Ok, up to you to upgrade pip

6. Create the initial website (optional)
```
cd wt00/
wagtail start mysite
cd mysite
pip install -r requirements.txt
python manage.py migrate
python manage.py createsuperuser
```
Once the admin user is created, we should be able to start the dev service
```
python manage.py runserver
```
And see the start page at [http://127.0.0.1:8000 ](http://127.0.0.1:8000)

Once succeeded - you should be able to navigate to the start page, and login to the admin interface. But there is not much fun there (yet).

Continue with [Tutorial for Wagtail v6.2.1](https://docs.wagtail.org/en/v6.2.1/getting_started/tutorial.html)

## Presentation example

Simple personal blog with images

Install git client:
```
sudo dnf install git-core
```

Checkout the code (https://github.com/epolkovnikov/wagtail101/tree/blog-6.2.1):
```
git clone https://github.com/epolkovnikov/wagtail101.git -bblog-6.2.1 blog-6.2.1
```
If you are curious - here is the delta between the base and the blog example: https://github.com/epolkovnikov/wagtail101/compare/base-6.2.1...blog-6.2.1

Copy-over the blog's branch mysite to the Wagtail mysite location.
One of the ways:
```
cp -r blog-6.2.1/mysite/. wt00/mysite/
```

Then make and execute migrations:
```
python manage.py makemigrations
python manage.py migrate
```
Once you start your server again
```
python manage.py runserver
```
The http://127.0.0.1:8000 will have not much. I will post a video next week

Canonical example is the [Bakery Shop](https://github.com/wagtail/bakerydemo)

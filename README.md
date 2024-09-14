# wagtail101
Materials for Wagtail basics; Python meetup presentation

## What is Wagtail?

They say it is the leading open-source Python Content Management System (CMS).

I'd say yes, it is a great "here is your box of parts, go assemble a CMS yourself".

If you expect install and run, - no it is not the case.

## Why Wagtail?

It is free and Open Source.

Building a blog with Django feels like rewriting a WordPress?

You want your users be completely isolated from the design part of it?

You already touched Django and want a boost with pre-built blocks?

You have a feature creep and have to integreate something unusual, or have it more like a Web app?

Or you have to give access to your data via an API along the pages?

You want to get your hands dirty with code.

Your Python is way better than your PHP.

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

   On Rocky 9:

   python 3.11, sqlite 3.26, wagtail 5.1.3 - somewhat better, yet, the choice is limited by the sqlite.

3. Install missing parts either to your system global env, or to your Python virtual env



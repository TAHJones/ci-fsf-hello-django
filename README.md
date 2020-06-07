<img src="https://codeinstitute.s3.amazonaws.com/fullstack/ci_logo_small.png" style="margin: 0;">

Welcome Thomas,

This is the Code Institute student template for Gitpod. We have preinstalled all of the tools you need to get started. You can safely delete this README.md file, or change it for your own project.

## Gitpod Reminders

To run a frontend (HTML, CSS, Javascript only) application in Gitpod, in the terminal, type:

`python3 -m http.server`

A blue button should appear to click: *Make Public*,

Another blue button should appear to click: *Open Browser*.

To run a backend Python file, type `python3 app.py`, if your Python file is named `app.py` of course.

A blue button should appear to click: *Make Public*,

Another blue button should appear to click: *Open Browser*.

In Gitpod you have superuser security privileges by default. Therefore you do not need to use the `sudo` (superuser do) command in the bash terminal in any of the backend lessons.

## Updates Since The Instructional Video

We continually tweak and adjust this template to help give you the best experience. Here are the updates since the original video was made:

**April 16 2020:** The template now automatically installs MySQL instead of relying on the Gitpod MySQL image. The message about a Python linter not being installed has been dealt with, and the set-up files are now hidden in the Gitpod file explorer.

**April 13 2020:** Added the _Prettier_ code beautifier extension instead of the code formatter built-in to Gitpod.

**February 2020:** The initialisation files now _do not_ auto-delete. They will remain in your project. You can safely ignore them. They just make sure that your workspace is configured correctly each time you open it. It will also prevent the Gitpod configuration popup from appearing.

**December 2019:** Added Eventyret's Bootstrap 4 extension. Type `!bscdn` in a HTML file to add the Bootstrap boilerplate. Check out the <a href="https://github.com/Eventyret/vscode-bcdn" target="_blank">README.md file at the official repo</a> for more options.

--------

Happy coding!


## Deployment

pip3 install django

So we're gonna CD into /workspace/.pip-modules/lib/python3.7/site-packages/
And then the site packages directory.
And if we now use the ls -la command in this directory to list out all of the files and directories inside it.

We can use a shortcut cd - to get back to the last directory that we were working in.

We'll type: django-admin startproject django_todo .

We can use that manage.py utility By typing: python3 manage.py runserver

Since we're going to build a to-do list. Let's create an app called todo

To do that we can type: python3 manage.py startapp todo

python3 manage.py makemigrations --dry-run

python3 manage.py showmigrations

python3 manage.py migrate --plan

python3 manage.py migrate

python3 manage.py createsuperuser


## Testing

pip3 install coverage

coverage run --source=todo manage.py test

coverage report

coverage html

python3 -m http.server


## Heroku

To install the Heroku cli follow the installation instructions at https://devcenter.heroku.com/articles/heroku-cli

heroku login


heroku - for list of commands e.g. apps

heroku apps help - to learn how the apps command works


## Postgres

To install postgres database - pip3 install psycopg2-binary

To install gunicorn or green unicorn - pip3 install gunicorn

## How to Deploy Project Using Heroku

1. Create a `requirements.txt` file from the terminal using the command `pip3 freeze --local > requirements.txt`.
2. Create a new app from the terminal using the following command `heroku apps:create your-app-name --region-eu`. The default region is the US , use the region flag to specify the region e.g `--region-eu` for Europe.
3. To check your app has been created use the command `heroku apps`. The new app should appear in your list of apps on Heroku.
4. To create a new postgres database on Heroku use the following command `heroku addons:create postgres?` Alternatively go to Heroku website and in the `resources` tab enter `postgres` in the `add-ons` search field and select `Heroku Postgres`. (To use mySQL database use an add on called `clear DB`)
5. To check that the postgres add on has been successfully installed use the command `heroku addons`.
6. To enable a connection to the remote postgres database install `dj-database_url` using the command `pip3 install dj-database_url`
7. Update the `requirements.txt` file to include `dj-database_url` using the command `pip3 freeze --local > requirements.txt`.
8. Use the command `heroku config` to get the postgres database url.
9. In the `dijango_todo` folder open `setting.py` and replace the default database settings:
Default database settings:
```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),
    }
}
```
Required postgres database settings::
```
DATABASES = {
    'default': dj_database_url.parse('postgres://xfyymrqjtkenvi:dd090438a7cc6d799db261e94fef5f14f484e0900e5100de14cc442fc2b58e06@ec2-18-210-214-86.compute-1.amazonaws.com:5432/d6kkrlomb6ohv7')
}
```
10. To import `dj_database_url` add `import dj_database_url` at the top of the `setting.py` file (directly underneath `import os`).
11. To transfer models and user information from default sqlite3 to postgres database use the command python3 `manage.py migrate`
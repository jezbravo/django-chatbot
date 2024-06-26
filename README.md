# DJANGO CHATBOT

## Description

This is a general-purpose chatbot application, similar to Open AI's famous ChatGPT, but instead uses Google's Gemini 1.0 Pro model. It also has the advantage of being able to be configured to provide personalized responses.

### Stack

- HTML
- CSS
- Django
- PostrgeSQL
- Railway

## Setup

First of all you must clone the repository:

```sh
git clone https://github.com/jezbravo/django-chatbot.git
cd django-chatbot
```

Create a virtual environment to install dependencies in and activate it:

```python
python.exe -m venv venv
.\venv\Scripts\activate
```

Then install the dependencies:

```python
(venv)pip install -r requirements.txt
```

Note the `(venv)` in front of the prompt. This indicates that this terminal session operates in a virtual environment set up by "venv".

### Environment Variables

To make the program work, it is necessary to configure the following environment variables in an **.env** file at the root of the project:

```python
SECRET_KEY=
GENAI_API_KEY=
DATABASE_URL=
```

The `SECRET_KEY` is the Django project key and can be generated by:

```python
(venv)python.exe .\manage.py shell

from django.core.management.utils import get_random_secret_key
print(get_random_secret_key())
```

The `GENAI_API_KEY` and the `DATABASE_URL` are provided by the Google API and by the database service (in this case, PostgreSQL) respectively.

### Database configuration

Perform the migration of the tables:

```python
(venv)python.exe .\manage.py migrate
```

Once everything is ready:

```python
(venv)python.exe .\manage.py runserver
```

And navigate to: http://localhost:8000/login

## Additional settings

### Administrator credentials

Run the following command:

```python
(venv)python.exe .\manage.py createsuperuser
```

and follow the instructions. Then navigate to: http://localhost:8000/admin and log in to manage the project from the Django administration panel.

### AI Assistant Name and Custom Responses

In the **views.py** file from "chatbot" folder, edit the ask_genai function, for example:

```python
   {
        "role": "user",
        "parts": ["You are an AI virtual assistant. Your name is Luna."]
    },
```

## Walkthrough

There are two simple login and register templates to access the chat page. Once inside, the virtual assistant will answer all questions and each user's conversation history will be stored privately so they can consult it.
You can test a version deployed to production at the following link: https://django-chatbot-production.up.railway.app/login

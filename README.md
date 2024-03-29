![django](https://github.com/descope-sample-apps/django-sample-app/assets/59460685/866222d2-437e-4f46-8d92-243ff9bd2d1c)

# Quillbot Django Sample App

Learn how to integrate Descope authentication in Django by building a [Quillbot](https://quillbot.com/) clone. 
This is a fork of https://github.com/descope-sample-apps/django-sample-app with a few
changes to setup, additional packages for CORS headers and WhiteNoise and a Procfile
so it can be easily deployed on Heroku.

Test deployment: https://quillbot.jamesf.xyz

Descope Django guide: https://www.descope.com/blog/post/auth-django-app

## ⚙️ Setup 

1. Clone the repository:

```
git clone https://github.com/jamesflores/Quillbot-Descope.git
```

2. Install dependencies:

```
pip3 install -r requirements.txt
```

3. Environment variables (.env file)

```
DESCOPE_PROJECT_ID=YOUR_DESCOPE_PROJECT_ID
```

- ```DESCOPE_PROJECT_ID```: can be found in your Descope's account under the [Project page](https://app.descope.com/settings/project)

4. Modify settings.py
- Add urls to CORS_ALLOWED_ORIGINS if running outside localhost
- Change SECRET_KEY if running in production

5. Descope Project Settings
- Add domain to which this app resides on (if not localhost)
- Add domain(s) to security section in "Approved Domains", click Save
- In the "Flows" section, ensure you are using the "New version" (in case you are reusing an old Descope project)

## 🔮 Running the Application 

To start the application, run:

```
python3 manage.py runserver
```

## 🥷 Roles  

Sign up for Descope and create admin roles [here](https://app.descope.com/authorization).

Create two roles in Descope, that will be mapped to Django permissions.
- is_staff
- is_superuser

Map these roles to any user you would like to make a staff or superuser in your Django app.
By default, any new registration will be a regular user.

## 🚀 Heroku Deployment
- The Procfile, requirements.txt and runtime.txt are used in deployment
- Ensure `DATABASE_URL` and `DESCOPE_PROJECT_ID` are set in config vars
- If using Cloudflare as your DNS and pointing to a custom domain, ensure Cloudflare proxy is off for your CNAME record (unless you are using Full SSL/TLS encryption mode, Flexible mode will not work due to CORS validation)

## ⚠️ Issue Reporting

For any issues or suggestions, feel free to open an issue in the GitHub repository.

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

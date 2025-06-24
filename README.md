# 🏥 Django Hospital Management System
This is a web-based **Hospital Management System** built with Django. It provides role-based access and functionality for **Admins**, **Doctors**, and **Patients**. The system includes features for appointments, discharges, contact forms, and user profile management.

![image](https://github.com/user-attachments/assets/3af743e8-bcd8-4acb-8701-4475174584a6)

![image](https://github.com/user-attachments/assets/e32901bc-bf7d-4c2e-9279-0d4ce4cab631)























---

## 🚀 Features

### 👨‍⚕️ Admin Panel
- Manage doctors, patients, appointments, and discharge records via Django Admin.
- Approve or reject user registrations (doctors/patients).
- View patient treatment costs.

### 👩‍⚕️ Doctor Dashboard
- View assigned patients.
- Manage patient appointments.
- View and update profile information.

### 🧑‍💼 Patient Dashboard
- Book appointments with available doctors.
- View appointment history.
- Request discharge.

### 📬 Contact Form
- Users can submit messages to the admin via a secure contact form
## 🧩 Tech Stack

- **Backend**: Django 3.0.5
- **Frontend**: HTML, CSS, Bootstrap (via templates)
- **Database**: SQLite3
- **Auth**: Django's built-in authentication
- **Email**: Gmail SMTP (configured in `settings.py`)
---

## 🏗️ Models Overview

### `Doctor`
- Linked to `User`
- Fields: department, mobile, profile_pic, address, status

### `Patient`
- Linked to `User`
- Fields: symptoms, assigned doctor ID, mobile, profile_pic

### `Appointment`
- doctorId and patientId (foreign key references by user ID)
- Fields: description, status, names, date

### `PatientDischargeDetails`
- Includes patient info, admission/release dates, costs, and totals

---

## 🛠️ Admin Setup

In `admin.py`, all models (`Doctor`, `Patient`, `Appointment`, `PatientDischargeDetails`) are registered using `ModelAdmin`.

```python
admin.site.register(Doctor, DoctorAdmin)
🧾 Forms Overview
Defined in forms.py:

AdminSignupForm, DoctorUserForm, PatientUserForm

Custom forms for profile updates and appointment creation

ContactusForm for sending messages

🖼️ Templates & Views
Views in views.py include:

home_view(): Home page

adminclick_view(), doctorclick_view(), patientclick_view(): Role-based access

custom_logout_view(): Logout logic

Each role has its own signup/login path and dashboard.

🔐 Authentication & Groups
Users are assigned to Django groups (Admin, Doctor, Patient)

Role-based logic handled via @user_passes_test
----------------------------------------------------

📂 Project Structure Highlights
cpp
Copy
Edit
hospitalmanagement/
├── hospital/
│   ├── models.py
│   ├── forms.py
│   ├── views.py
│   ├── admin.py
│   ├── templates/
│   └── static/
├── hospitalmanagement/
│   ├── settings.py
│   └── urls.py
├── manage.py
----------------------------------------------------
📸 Profile Picture Uploads
Doctors and Patients can upload profile pictures.

Images are saved under:

profile_pic/DoctorProfilePic/

profile_pic/PatientProfilePic/
----------------------------------------------------
## 📦 Installation Instructions

### 1. Clone the repository

git clone https://github.com/TheUnshackled1/Centro_Django.git
cd hospitalmanagement
2. Create a virtual environment and activate it
bash
Copy
Edit
python -m venv venv
venv\Scripts\activate  # On Windows
# OR
source venv/bin/activate  # On macOS/Linux
3. Install dependencies
If you have a requirements.txt file:


Copy
Edit
pip install -r requirements.txt
Or manually install required packages:


Copy
Edit
pip install django==3.0.5
pip install django-widget-tweaks
4. Run database migrations

Copy
Edit
python manage.py makemigrations
python manage.py migrate
5. Create a superuser (admin login)

Copy
Edit
python manage.py createsuperuser
Follow the prompts to set up username, email, and password.

6. Run the development server

Copy
Edit
python manage.py runserver
7. Open in your browser
Go to: http://127.0.0.1:8000

✅ You're now ready to use the Hospital Management System locally!

ℹ️ Note: Make sure to add widget_tweaks to your INSTALLED_APPS in settings.py if it's not already present:

python
Copy
Edit
INSTALLED_APPS = [
    ...
    'widget_tweaks',
]

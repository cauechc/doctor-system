**Django Patient Management System**
This is a Django-based system for managing patients, consultations, and related tasks. It allows a doctor to:

Register patients with their personal details.
Record their mood during consultations.
Upload related videos for consultations.
Update the patient’s payment status.
Display public consultations if the patient has an active payment status.

**Features:**

Patient Registration: Register new patients by providing their name, email, phone number, and complaint, along with a photo.
Consultation Records: For each patient, consultations can be added, including mood tracking and video uploads.
Patient Management: Doctors can update patient payment statuses.
Public Consultation View: Display a public consultation if the patient has an active payment status.
Task Management: Tasks can be assigned to patients and linked to consultations.

**Requirements:**
Python 3.6+
Django 5.1.6 or higher

**Setup:**
**Clone the repository:**
bash
Copy
git clone <repository_url>
cd <repository_directory>

**Install dependencies:** Create a virtual environment and install required packages.
bash
Copy
python -m venv venv
source venv/bin/activate   # On Windows use `venv\Scripts\activate`
pip install -r requirements.txt

**Migrate the database:** Run the following command to create the necessary database tables.
bash
Copy
python manage.py migrate

**Create a superuser (for accessing the Django admin panel):**
bash
Copy
python manage.py createsuperuser

**Run the development server: Start the Django development server.**
bash
Copy
python manage.py runserver
The application will be available at http://127.0.0.1:8000/.

**URL Configuration:**
**Root URL (/):**
Lists all registered patients.
Accessible via the pacientes view.

**Patient Detailed View (/<int:id>):**
Shows detailed information of a specific patient based on the id.
Allows the doctor to add a consultation, track mood, and upload a video for the patient.

**Update Patient (/atualizar_paciente/<int:id>):**
Updates the payment status for the given patient (id).
The payment status can be updated to "active" or "inactive".

**Delete Consultation (/excluir_consulta/<int:id>):**
Allows the deletion of a specific consultation by its id.

**Public Consultation (/consulta_publica/<int:id>):**
Displays a public view of the consultation if the patient has an active payment status.
If the patient does not have an active payment status, a 404 error is raised.

**Models:**
**Patient (Pacientes):**
Fields: name, email, phone, complaint, photo, payment_status
**Consultation (Consultas):**
Fields: mood, general_record, video, tasks, patient (Foreign Key to Pacientes)
**Task (Tarefas):**
Used to associate tasks with consultations.

**Admin Interface:**
The Django admin panel can be used to manage patients, consultations, and tasks.
To access the admin panel, navigate to: http://127.0.0.1:8000/admin/
Log in with the superuser credentials created during the setup process.

**Notes:**
Ensure that media files (such as patient photos and consultation videos) are properly configured in the settings.py file to be stored and served correctly.
This application assumes that patients must have an "active" payment status to view public consultations.

**Contributing:**
Fork the repository.
Create a feature branch (git checkout -b feature-branch).
Commit your changes (git commit -am 'Add new feature').
Push to the branch (git push origin feature-branch).
Create a pull request.

**License:**
This project is licensed under the MIT License - see the LICENSE file for details.

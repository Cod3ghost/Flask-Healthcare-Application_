
# Flask-Health-Application

This is a Flask-based web application designed to collect data on users' income and spending patterns. The data will be used to analyze spending trends in preparation for a new healthcare product launch. This project includes a web form to gather user data and stores it in a MongoDB database.

## Features
- Collect user data (age, gender, total income, and various expenses).
- Store data in a MongoDB database for analysis.
- Deploy on AWS EC2 instance for remote access.

## Table of Contents
- [Installation](#installation)
- [Running Locally](#running-locally)
- [Deploying to AWS EC2](#deploying-to-aws-ec2)
- [Updating the Application](#updating-the-application)
- [License](#license)

---

## Installation

1. **Clone the Repository**:
   Clone this repository to your local machine or EC2 instance.

   ```bash
   git clone https://github.com/yourusername/Flask-Health-Application.git
   ```

2. **Navigate to the Project Directory**:
   ```bash
   cd Flask-Health-Application
   ```

3. **Set Up a Virtual Environment**:
   Create and activate a virtual environment to isolate dependencies.

   ```bash
   python3 -m venv venv
   source venv/bin/activate  # On macOS and Linux
   venv\Scripts\activate  # On Windows
   ```

4. **Install Dependencies Individually**:
   Manually install each required dependency:

   ```bash
   pip install flask
   pip install pymongo
   ```

5. **Configure MongoDB**:
   Ensure MongoDB is running locally, or use a MongoDB Atlas connection. Update the MongoDB connection string in `app.py` if needed.

---

## Running Locally

1. **Start the Flask Application**:
   Run the app locally to test it.

   ```bash
   python app.py
   ```

2. **Access the App**:
   Open a browser and go to `http://127.0.0.1:5000` to view the application.

---

## Deploying to AWS EC2

1. **Launch an EC2 Instance**:
   - Create an EC2 instance in AWS.
   - Choose an Ubuntu instance and configure security settings to allow traffic on port `5000` (or the port you’re using).

2. **SSH into the EC2 Instance**:
   Use the SSH command below (replace `your-key.pem` and `your-ec2-public-ip` with your actual key and IP).

   ```bash
   ssh -i your-key.pem ubuntu@your-ec2-public-ip
   ```

3. **Clone the Repository on EC2**:
   If you haven’t cloned the repository, do it now:

   ```bash
   git clone https://github.com/yourusername/Flask-Health-Application.git
   cd Flask-Health-Application
   ```

4. **Set Up the Virtual Environment and Install Dependencies**:
   ```bash
   python3 -m venv venv
   source venv/bin/activate
   pip install flask pymongo
   ```

5. **Run the Flask App on EC2**:
   Set Flask to listen on all IP addresses to make it accessible remotely:

   ```python
   # In app.py
   if __name__ == "__main__":
       app.run(host="0.0.0.0", port=5000)
   ```

   Start the app:

   ```bash
   python app.py
   ```

6. **Access the App**:
   In your browser, go to `you-public-ipaddress:5000`.

---

## Updating the Application

1. **Make Changes to Your Code Locally**:
   - After making changes, commit and push the updates to your Git repository.

   ```bash
   git add .
   git commit -m "Describe your changes"
   git push origin main
   ```

2. **Pull Updates on EC2**:
   SSH into your EC2 instance, navigate to the project directory, and pull the latest changes:

   ```bash
   cd /path/to/your/project
   git pull origin main
   ```

3. **Restart the Application**:
   Stop the existing Flask app (if running) and restart it to apply the changes.

---

## License

This project is licensed under the MIT License. See `LICENSE` for more details.

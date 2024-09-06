# Job Portal with Automation

A web-based job portal that facilitates job application and listing management for job seekers and employers. The platform includes role-based access control, user authentication and authorization, automated email notifications, and CRUD operations for job postings and applications.

## Features

- **User Authentication & Authorization**: Secure login and registration using JWT (JSON Web Tokens) and role-based access control (Employer and Job Seeker).
- **Job Management**:
  - Employers can post, update, delete, and view job listings.
  - Job seekers can view all job listings, filter by location or domain, and apply for jobs.
- **Application Management**:
  - Job seekers can apply for jobs and view their applications.
  - Employers can view all applications for their job postings.
- **Automated Email Notifications**: Job seekers receive automated emails for new job postings matching their preferences.
- **Error Handling & Security**: Centralized error handling and secure HTTP-only cookies.
- **Cron Job Automation**: Automated tasks like sending newsletters using `node-cron`.

## Tech Stack

- **Backend**: Node.js, Express.js
- **Database**: MongoDB
- **Authentication**: JWT (JSON Web Tokens)
- **File Upload**: Cloudinary, express-fileupload
- **Email Notifications**: Nodemailer
- **Task Automation**: Node-cron
- **Other Libraries**: cookie-parser, dotenv, cors, mongoose

## Installation

1. **Clone the repository**:

    ```bash
    git clone https://github.com/yourusername/your-repo.git
    cd your-repo
    ```

2. **Install the dependencies**:

    ```bash
    npm install
    ```

3. **Configure Environment Variables**:

    Create a `.env` file in the root directory and add the following:

    ```env
    PORT=5000
    MONGO_URI=your_mongo_uri
    JWT_SECRET_KEY=your_jwt_secret
    COOKIE_EXPIRE=7
    SMTP_HOST=smtp.example.com
    SMTP_PORT=587
    SMTP_SERVICE=Gmail
    SMTP_MAIL=your_email@example.com
    SMTP_PASSWORD=your_email_password
    CLOUDINARY_CLOUD_NAME=your_cloudinary_name
    CLOUDINARY_API_KEY=your_cloudinary_api_key
    CLOUDINARY_API_SECRET=your_cloudinary_api_secret
    FRONTEND_URL=http://localhost:3000
    ```

4. **Run the application**:

    ```bash
    npm start
    ```

    The server will start at `http://localhost:5000`.

## API Endpoints

### User Routes

- **POST** `/api/v1/user/register` - Register a new user.
- **POST** `/api/v1/user/login` - User login.
- **GET** `/api/v1/user/logout` - User logout.
- **GET** `/api/v1/user/getuser` - Get current user details.
- **PUT** `/api/v1/user/update/profile` - Update user profile.
- **PUT** `/api/v1/user/update/password` - Update user password.

### Job Routes

- **POST** `/api/v1/job/post` - Post a new job (Employer only).
- **GET** `/api/v1/job/getall` - Get all job listings.
- **GET** `/api/v1/job/getmyjobs` - Get jobs posted by the current employer.
- **GET** `/api/v1/job/get/:id` - Get a specific job by ID.
- **DELETE** `/api/v1/job/delete/:id` - Delete a job (Employer only).

### Application Routes

- **POST** `/api/v1/application/post/:id` - Apply for a job (Job Seeker only).
- **GET** `/api/v1/application/employer/getall` - Get all applications for the employer's jobs.
- **GET** `/api/v1/application/jobseeker/getall` - Get all applications made by the job seeker.
- **DELETE** `/api/v1/application/delete/:id` - Delete an application.

## Running Tests

To run tests, use the following command:

```bash
npm test

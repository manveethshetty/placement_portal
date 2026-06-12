# Campus Placement Management System

A web-based placement management system built with Flask and MySQL.
Manages student applications, placement drives, and TPO operations
with full database-level policy enforcement.

## Tech Stack
- **Backend:** Flask (Python)
- **Database:** MySQL 8.x (InnoDB)
- **Frontend:** HTML5, CSS3, Bootstrap 5
- **Templating:** Jinja2

## Features
- Student portal — view drives, apply, track application status
- TPO Officer portal — manage drives, shortlist, update results
- One-student-one-company policy enforced via stored procedure
- Automatic audit trail on every status change via triggers
- CGPA and eligibility checks enforced at database level
- Role-based access control (Student vs TPO)
- SQL injection prevention via parameterised queries

## Database Design
- 11 tables fully normalised to 3NF
- 2 views — `vw_drive_listing`, `vw_application_details`
- 2 AFTER triggers for automatic status history logging
- 1 stored procedure `sp_update_status` for placement policy enforcement
- Named constraints — CHECK, UNIQUE, FOREIGN KEY, ON DELETE CASCADE

## Setup
1. Clone the repo
   ```
   git clone https://github.com/manveethshetty/placement_portal
   cd placement_portal
   ```
2. Create the database
   ```
   mysql -u root -p < schema.sql
   ```
3. Install dependencies
   ```
   pip install -r requirements.txt
   ```
4. Run the app
   ```
   python app.py
   ```
5. Open `http://localhost:5000`

## Roles
| Role | Credentials |
|------|-------------|
| Student | Register via signup page |
| TPO Officer | Pre-seeded in database via schema.sql |

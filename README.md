from datetime import datetime

class Address:
    def __init__(self, street, city, state, zip_code):
        self.street = street
        self.city = city
        self.state = state
        self.zip_code = zip_code

    def get_full_address(self):
        return f"{self.street}, {self.city}, {self.state} {self.zip_code}"

class Department:
    def __init__(self, department_id, name, location):
        self.department_id = department_id
        self.name = name
        self.location = location
        self.employees = []

    def add_employee(self, employee):
        self.employees.append(employee)

    def get_department_name(self):
        return self.name

    def get_location(self):
        return self.location

class Role:
    def __init__(self, role_id, title, description):
        self.role_id = role_id
        self.title = title
        self.description = description

    def get_role_title(self):
        return self.title

    def get_role_description(self):
        return self.description

class Project:
    def __init__(self, project_id, name, description, start_date, end_date):
        self.project_id = project_id
        self.name = name
        self.description = description
        self.start_date = start_date
        self.end_date = end_date
        self.employees = []

    def add_employee(self, employee):
        self.employees.append(employee)

    def get_project_details(self):
        return f"Project: {self.name} ({self.description})"

    def get_duration(self):
        duration = self.end_date - self.start_date
        return duration.days

class Timesheet:
    def __init__(self, timesheet_id, date, hours_worked, employee):
        self.timesheet_id = timesheet_id
        self.date = date
        self.hours_worked = hours_worked
        self.employee = employee

    def get_timesheet_details(self):
        return f"Date: {self.date}, Hours Worked: {self.hours_worked}"

    def get_hours_worked(self):
        return self.hours_worked

class Employee:
    def __init__(self, employee_id, first_name, last_name, email, phone, address):
        self.employee_id = employee_id
        self.first_name = first_name
        self.last_name = last_name
        self.email = email
        self.phone = phone
        self.address = address
        self.department = None
        self.projects = []
        self.roles = []
        self.timesheets = []

    def set_department(self, department):
        self.department = department

    def add_project(self, project):
        self.projects.append(project)

    def add_role(self, role):
        self.roles.append(role)

    def add_timesheet(self, timesheet):
        self.timesheets.append(timesheet)

    def get_full_name(self):
        return f"{self.first_name} {self.last_name}"

    def get_email(self):
        return self.email

    def get_phone(self):
        return self.phone

    def get_address(self):
        return self.address

def main():
    # Input address details
    street = input("Enter street address: ")
    city = input("Enter city: ")
    state = input("Enter state: ")
    zip_code = input("Enter zip code: ")
    address = Address(street, city, state, zip_code)

    # Input department details
    department_id = int(input("Enter department ID: "))
    department_name = input("Enter department name: ")
    department_location = input("Enter department location: ")
    department = Department(department_id, department_name, department_location)

    # Input role details
    role_id = int(input("Enter role ID: "))
    role_title = input("Enter role title: ")
    role_description = input("Enter role description: ")
    role = Role(role_id, role_title, role_description)

    # Input project details
    project_id = int(input("Enter project ID: "))
    project_name = input("Enter project name: ")
    project_description = input("Enter project description: ")
    start_date = datetime.strptime(input("Enter project start date (YYYY-MM-DD): "), "%Y-%m-%d")
    end_date = datetime.strptime(input("Enter project end date (YYYY-MM-DD): "), "%Y-%m-%d")
    project = Project(project_id, project_name, project_description, start_date, end_date)

    # Input employee details
    employee_id = int(input("Enter employee ID: "))
    first_name = input("Enter first name: ")
    last_name = input("Enter last name: ")
    email = input("Enter email: ")
    phone = input("Enter phone number: ")
    employee = Employee(employee_id, first_name, last_name, email, phone, address)
    employee.set_department(department)
    employee.add_role(role)
    employee.add_project(project)

    # Input timesheet details
    timesheet_id = int(input("Enter timesheet ID: "))
    timesheet_date = datetime.strptime(input("Enter timesheet date (YYYY-MM-DD): "), "%Y-%m-%d")
    hours_worked = float(input("Enter hours worked: "))
    timesheet = Timesheet(timesheet_id, timesheet_date, hours_worked, employee)
    employee.add_timesheet(timesheet)

    # Print employee details
    print("Employee:", employee.get_full_name())
    print("Email:", employee.get_email())
    print("Phone:", employee.get_phone())
    print("Address:", employee.get_address().get_full_address())
    print("Department:", department.get_department_name())
    print("Project:", project.get_project_details())
    print("Timesheet:", timesheet.get_timesheet_details())

if __name__ == "__main__":
    main()

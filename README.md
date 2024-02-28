# recipi-app-api
Recipi API project

19 api endpoints
    managing users, recipes, tags, ingredients
user authentication

browsable admin interface (django admin)

browsable api (swagger)



Apps
> app/ - Django project
> app/core/ - Code shared between multiple apps
> app/user/ - User related code
> app/recipe/ - Recipe related code


Unit Tests
> Code which tests code
  - sets up conditions/ inputs
  - Runs a piece of code
  - Checks outputs with "assertions"
> Many benefits
  - Ensures code runs as expected
  - Catches bugs
  - Improves reliability
  - Provides confidence


What is TDD?(test driven develop)
> Development practice
Write test -> Run Test -> Add feature -> run test -> re-factor

Why use TDD?
> Better understanding of code
> Make changes with confidence
> Reduces bugs

Why use Docker?
> Consistent dev and prod environment
> Easier collaboration
> Capture all dependencies as code
  - Python requirements
  - Operating system dependencies
> Easier cleanup

How we'll use Docker
> Define Dockerfile
> Create Docker Compose configuration
> Run all commands

Configuring Docker
> create a Dockerfile
> Lists steps for creating image
  - choose a base image
  - install dependencies
  - setup users

Docker Compose
> how our Docker images should be used
> Define our services
  - Name
  - Port mappings
  - Volume mappings

docker-compose run --rm app sh -c "py manage.py collectstatic"

docker-compose : runs a Docker Compose command
run : will start a specific container defined in config
--rm : removes teh container
app : the name of the service
sh -c : passes in a shell command
py~ : command to run inside container

What is Linting?
> tool to check code formatting
> highlights errors, typos, formatting issues

How we'll handling Linting
> Install flake8 package
> Run it through Docker Compose
docker-compose run --rm app sh -c "flake8" 명령어로 확인
docker-compose run --rm app sh -c "python manage.py test"


What is Github Actions?
> Automation tool
> Similar to Travis-Ci, Gitlab CI/CD, Jenkins
> Run jobs when code changes
> Automation tasks
common use - deployment, code linting, unit tests

How it works
push to github -> run unit tests -> success/fail

Django test framework
> Based on the unittest library
> Django adds features
  - Test client - dummy web browser
  - simulate authentiation
  - temporary database
> Django REST framework adds features
  - API test client

Where do you put tests?
> Placeholder tests.py added to each app
> or create tests/ subdirectory to split tests up
> Test modules must start with test_
> Test directories must contain __init__.py

Test Database
> Test code that uses the DB
> Specific database for tests
> Happens for every test

Test classes
> SimpleTestCase
  - No database integration
  - Useful if no database is required for test
  - Save time executing tests
> TestCase
  - Database integration
  - Useful for using database in code

Writing tests
> Import test class
  - SimpleTestCase - No Database
  - TestCase - Database
> Import objects to test
> Define test class
> Add test method
> Execute code to be tested
> Check output

What is Mocking?
> Override or change behaviour of dependencies
> Avoid uninteded side effects
> Isolate code being tested

Why use Mocking?
> Avoid relying on external services
  - Can't guarantee they will be available
  - Makes tests unpredictable and inconsistent
> Avoid uninteded consequences
  - Accidentally sending emails
  - Overloading external services
> Speed up tests

How to mock code?
> Use unittest.mock
  - MagicMock/Mock - Replace real objects
  - patch - Overrides code for tests

Database Migration
Django ORM
>  Object Relational Mapper(ORM)
> Abstraction layer for data
  - DJango handles database structure and changes
  - Focus on Python code
  - Use any database (within reason)

Creating migrations
> Ensure app is enables in settings.py
> Use Django CLI
  - python manage.py migrate
> Run it after waiting for database


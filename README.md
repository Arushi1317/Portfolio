Experiment 3: Branches and Merging in Git
Goal: Create two branches, modify a file in each, then merge into main.
 
Step-by-Step
Step 1 – Start from main branch:
git checkout main
 
Step 2 – Create and switch to branch1:
git checkout -b branch1
📌 Note: git checkout -b creates a new branch AND switches to it.
 
Step 3 – Modify the file in branch1:
echo "Change from branch1" >> hello.txt
git add hello.txt
git commit -m "Changes from branch1"
 
Step 4 – Switch back to main and create branch2:
git checkout main
git checkout -b branch2
 
Step 5 – Modify the file in branch2:
echo "Change from branch2" >> hello.txt
git add hello.txt
git commit -m "Changes from branch2"
 
Step 6 – Merge branch1 into main:
git checkout main
git merge branch1
 
Step 7 – Merge branch2 into main:
git merge branch2
 
Step 8 – View final file:
cat hello.txt

Commands used till Part A
git init
echo "Hello Git" > hello.txt
git add .
git commit -m "Initial commit"
git branch -M main

git remote add origin https://github.com/Arushi1317/pra4.git
git push -u origin main

git checkout -b feature-branch
echo "Feature work" >> hello.txt
git add .
git commit -m "Feature update"
git push origin feature-branch
Then on GitHub:
Compare & pull request
Create pull request
Merge pull request
Confirm merge

EXPERIMENT 5 

practice
└── .github
    └── workflows
        └── hello.yml

git init
git add .
git commit -m "initial commit"
git add .github/
git status
git commit -m "Add GitHub Actions workflow"
 git remote add origin https://github.com/Arushi1317/prac5.git   
Git push -u origin main

name: Hello World Workflow

on:
  push:
    branches: [ main ]

jobs:
  greet:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Print Success Message
        run: echo 'Build Successful! Workflow triggered on push.'

 Check in git actions


EXP 7 PYTHON 
 test_math.py
from math_ops import add

def test_add():
   assert add(2, 3) == 5
   assert add(0, 0) == 0
   print("All tests passed!")

test_add()

math_ops.py
def add(a, b):
   return a + b

EXPERIMENT 8

Step 1 – Create your app file (app.py):
from flask import Flask
app = Flask(__name__)
 
@app.route('/')
def home():
	return 'Hello from Docker!'
 
if __name__ == '__main__':
	app.run(host='0.0.0.0', port=5000)
 
Step 2 – Create requirements.txt:
flask
 
Step 3 – Create the Dockerfile (no extension):
FROM python:3.9-slim
 
WORKDIR /app
 
COPY requirements.txt .
RUN pip install -r requirements.txt
 
COPY . .
 
EXPOSE 5000
 
CMD ["python", "app.py"]
 
Step 4 – Build the Docker image:
docker build -t myflaskapp .
📌 Note: The dot (.) means 'use the Dockerfile in the current directory'.
 
Step 5 – Run the container:
docker run -p 5000:5000 myflaskapp
 
Step 6 – Open browser and visit: http://localhost:5000

EXPERIMENT 9
Step 2: Create project folder
mkdir compose-demo
cd compose-demo

Step 3: Create docker-compose.yml
Create a file named:
docker-compose.yml
Inside the compose-demo folder.

Step 4: Paste this code in docker-compose.yml
services:
 web:
   image: nginx:latest
   ports:
     - '8080:80'
   depends_on:
     - db

 db:
   image: mysql:5.7
   environment:
     MYSQL_ROOT_PASSWORD: rootpassword
     MYSQL_DATABASE: mydb
   ports:
     - '3307:3306'
Note: I used 3307:3306 because port 3306 was already busy on your system.

Step 5: Start containers
Run this inside the same folder where docker-compose.yml exists:
docker compose up -d
Meaning:
up = start containers
-d = detached/background mode

Step 6: Check running containers
docker compose ps
Expected output should show:
compose-demo-web-1    nginx:latest    Up
compose-demo-db-1     mysql:5.7       Up

Step 7: Open output in browser
Open:
http://localhost:8080
Expected output:
Welcome to nginx!
This is the final output for the experiment.

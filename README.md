TASKS:

 

Must accurately determine the availability of all endpoints during every check cycle

- Endpoints are only considered available if they meet the following conditions

- Status code is between 200 and 299

- Endpoint responds in 500ms or less

 

Must return availability by domain

Must ignore port numbers when determining domain

Must determine availability cumulatively

Check cycles must run and log availability results every 15 seconds regardless of the number of endpoints or their response times

 

Readme

- Must outline how to install and run the code

- Must include a section that outlines how each of the issues were identified and why each change to the code was made

 

# HOW TO RUN:

1. Create and activate a Python virtual environment:

   ```bash

   # Create a new virtual environment

   python3 -m venv venv

  

   # Activate the virtual environment

   source venv/bin/activate   # On macOS/Linux

   ```

 

2. Install required dependencies:

   ```bash

   pip install -r requirements.txt

   ```

 

3. Run the script with your YAML configuration file:

   ```bash

   python main.py sample.yaml

   ```

 

4. To deactivate the virtual environment when finished:

   ```bash

   deactivate

   ```

 

# HOW EACH ISSUE IDENTIFIED:

 

First ran the file after pip installing, ran into this error:

monitor_endpoints(config_file)

 

method=method.upper(),

           ^^^^^^^^^^^^

AttributeError: 'NoneType' object has no attribute 'upper'

 

Following the task's ask, I added  'GET')  # Add default 'GET' if method is not specified to line 14.

 

That fixed that error.

 

Now when I run the script I see,

python main.py sample.yaml

dev-sre-take-home-exercise-rubric.us-east-1.recruiting-public.fetchrewards.com has 25% availability percentage

---

dev-sre-take-home-exercise-rubric.us-east-1.recruiting-public.fetchrewards.com has 25% availability percentage

---

 

very slow. now add the 500 ms timeout requirement.

 

I edited lines 18-25 with the timeout

 

lines 27- 34 i added more accurate error handling

 

noticed the line,  print("Usage: python monitor.py <config_file_path>") in the bottom init prob has legacy mention of the file and prob should be changed to main.py. since when doing this take home  I dont see a monitor.py

 

lets do port splitting handling now

 

edit lines 44 and 45 to do domain handling of ports.

 

might as well fix usage message error.

 

did that. just disqualify me i am trying out copilot for the first time. i only work in vim and terminal for a majority of my life and i dont use an IDE so this is interesting to me. this shit magic.

 

now i want to fix the check_health method for better outputs.

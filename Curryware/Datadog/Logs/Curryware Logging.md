#### Python Code

`# Setting Logging that Datadog can pick up.  
logFormatter = json_log_formatter.JSONFormatter()  
json_handler = logging.FileHandler('/var/log/currywareff.json')  
json_handler.setFormatter(logFormatter)  
  
logger = logging.getLogger(__name__)  
logger.addHandler(json_handler)  
logger.setLevel(logging.DEBUG)`

#### Agent Setup
- Create conf.yaml in <agent folder>/conf.d/python.d (make sure to indent correctly)

```init_config:

  

instances:

  

# Log section

logs:

  

- type: file

path: "/Users/scotc/var/log/currywareff.json"

service: "currywareff"

source: python

sourcecategory: sourcecode```
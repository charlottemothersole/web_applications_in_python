# {{ NAME }} Route Design Recipe

_Copy this design recipe template to test-drive a plain-text Flask route._
<!-- --------------------------------- -->
Use this Design Recipe to test-drive a new route POST /sort-names which receives a list of names (as a comma-separated string) and return the same list, sorted in alphabetical order.

Here's a description of the expected behaviour:

<!-- ---------------------------------- -->
## 1. Design the Route Signature

_Include the HTTP method, the path, and any query or body parameters._


<!-- # Sort names route
POST /add_names
  names: string -->


# sorting_names route
GET /names?add=Eddie,Leo

<!-- # Submit message route
POST /submit
  name: string
  message: string -->


<!-- # Request:
POST http://localhost:5000/sort-names

# With body parameters:
names=Joe,Alice,Zoe,Julia,Kieran -->

# Expected response (sorted list of names):
Alice, Eddie, Julia, Karim, Leo
```

## 2. Create Examples as Tests

_Go through each route and write down one or more example responses._

_Remember to try out different parameter values._

_Include the status code and the response body._

```python
# EXAMPLE

# GET /home
#  Expected response (200 OK):
"""
This is my home page!
"""

# GET /wave?name=Leo
#  Expected response (200 OK):
"""
I am waving at Leo
"""

# GET /wave
#  Expected response (200 OK):
"""
I am waving at no one!
"""

# POST /submit
#  Parameters:
#    name: Leo
#    message: Hello world
#  Expected response (200 OK):
"""
Thanks Leo, you sent this message: "Hello world"
"""

# POST /submit
#  Parameters: none
#  Expected response (400 Bad Request):
"""
Please provide a name and a message


GET /names?add=Eddie,Leo
 Parameters:none
 Expected response (200 OK):

'Alice, Eddie, Julia, Karim, Leo'



## 3. Test-drive the Route

_After each test you write, follow the test-driving process of red, green, refactor to implement the behaviour._

Here's an example for you to start with:

```python
"""
GET /home
  Expected response (200 OK):
  "This is my home page!"
"""
def test_get_home(web_client):
    response = web_client.get('/home')
    assert response.status_code == 200
    assert response.data.decode('utf-8') == 'This is my home page!'

"""
POST /submit
  Parameters:
    name: Leo
    message: Hello world
  Expected response (200 OK):
  "Thanks Leo, you sent this message: "Hello world""
"""
def test_post_submit(web_client):
    response = web_client.post('/submit', data={'name': 'Leo', 'message': 'Hello world'})
    assert response.status_code == 200
    assert response.data.decode('utf-8') == 'Thanks Leo, you sent this message: "Hello world"'

"""
POST /sort_names
  Parameters:
    names: Joe,Alice,Zoe,Julia,Kieran
  Expected response (200 OK):
  "Alice,Joe,Julia,Kieran,Zoe"
"""
def test_post_sort_names(web_client):
    response = web_client.post('/sort_names', data={'names': 'Joe,Alice,Zoe,Julia,Kieran'})
    assert response.status_code == 200
    assert response.data.decode('utf-8') == 'Alice,Joe,Julia,Kieran,Zoe'
```

GET /names?add=Eddie,Leo
 Parameters:none
 Expected response (200 OK):

'Alice, Eddie, Julia, Karim, Leo'

def test_get_add_names(web_client):
    response = web_client.get('/names?add=Eddie,Leo')
    assert response.status_code == 200
    assert response.data.decode('utf-8') = 'Alice, Eddie, Julia, Karim, Leo'

<!-- BEGIN GENERATED SECTION DO NOT EDIT -->

---

**How was this resource?**  
[😫](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fweb-applications-in-python&prefill_File=resources%2Fplain_route_recipe_template.md&prefill_Sentiment=😫) [😕](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fweb-applications-in-python&prefill_File=resources%2Fplain_route_recipe_template.md&prefill_Sentiment=😕) [😐](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fweb-applications-in-python&prefill_File=resources%2Fplain_route_recipe_template.md&prefill_Sentiment=😐) [🙂](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fweb-applications-in-python&prefill_File=resources%2Fplain_route_recipe_template.md&prefill_Sentiment=🙂) [😀](https://airtable.com/shrUJ3t7KLMqVRFKR?prefill_Repository=makersacademy%2Fweb-applications-in-python&prefill_File=resources%2Fplain_route_recipe_template.md&prefill_Sentiment=😀)  
Click an emoji to tell us.

<!-- END GENERATED SECTION DO NOT EDIT -->
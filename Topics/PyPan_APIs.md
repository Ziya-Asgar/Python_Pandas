# Pandas and Web APIs

---

There are a number of ways to access public APIs from Python; one method is the `requests` package, which is an external package and needs to be installed.

To send a GET request to a url, we use the `requests.get` method. It's a good practice to always call `raise_for_status` after using `requests.get` to check for HTTP errors.

```py
import requests

url = "https://api.github.com/repos/pandas-dev/pandas/issues"

resp = requests.get(url)
resp.raise_for_status()

print(resp) # <Response [200]>
```

We can use response object’s `json` method to parse JSON data as a dictionary or list (depending on what JSON is returned). We can then pass the returned data directly to `DataFrame` and extract fields of interest:

```py
import pandas as pd
import requests

url = "https://api.github.com/repos/pandas-dev/pandas/issues"

resp = requests.get(url)
resp.raise_for_status()

data = resp.json()
print(type(data)) # list

issues = pd.DataFrame(data, columns=["number", "title", "labels", "state"])
print(issues)
```

Hence, we can easily interact with a web API using the `requests` package and create a dataframe from the returned data using the `pandas`.

---

---

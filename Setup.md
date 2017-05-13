The following steps need to be performed to set up Expipe in CINPLA:

- [Setup Norstore](CINPLA_setup_Norstore)
- [Install Anaconda](https://www.continuum.io/downloads)
- Open a terminal with Anaconda
- Install expipe and the other applications: 

    ```
    conda create -n expipe
    source activate expipe
    conda install expipe expipe-cli expipe-browser exdir-cli exdir-browser expipe-io-neuro pyxona exana -c defaults -c cinpla/label/dev -c cinpla -c conda-forge
    pip install pyrebase
    ```

- *Only if you are on Linux*, do the following (because there is a bug with OpenGL in PyQt):

    ```
    pip install pyqt5==5.7.1 sip==4.19
    ```

- Open Jupyter Notebook: `jupyter notebook`
- Configure expipe by running the following code in the notebook. Add your email and password before running the code.

```python
import expipe
expipe.configure(
    data_path="w:\\server",
    email="<write your email here>",
    password="<write your password here>",
    url_prefix="expipe-26506",
    api_key="AIzaSyAjGqZwiCKS2333m820e9UdZ7jbnkfEpjw"
)
```
You might need to change the data_path if you have a different path to Norstore. On Linux this should be `/media/norstore/server`.

## Config file ##

If you want to copy and paste the config, here is an example config file:

```yaml
data_path: w:\\server
server:
  data_path: /norstore_osl/projects/NS9048K/server
  username: <norstore username>
  hostname: login.norstore.uio.no
firebase:
  email: your@email.com
  password: yourpassword
  config:
    apiKey: AIzaSyAjGqZwiCKS2333m820e9UdZ7jbnkfEpjw
    authDomain: expipe-26506.firebaseapp.com
    databaseURL: https://expipe-26506.firebaseio.com
    storageBucket: expipe-26506.appspot.com
```

## Testing ##

**WARNING**: Tests can be destructive and have to be run on a different server. Use `expipe-debug.firebaseio.com` for testing.

A separate config file needs to be created if you want to run tests. The config file needs to be placed in `~/.config/expipe/test-config.yaml` and must have the key `allow_tests: true`. Here is an example:

```yaml
allow_tests: true
data_path: '/tmp/expipe-data'
firebase:
  email: <needs to be changed>
  password: <needs to be changed>
  config:
    apiKey: AIzaSyBnbsraKxrO8zv1qVZeAvJR4fEWzExQhOM
    authDomain: expipe-debug.firebaseapp.com
    databaseURL: https://expipe-debug.firebaseio.com
    storageBucket: expipe-debug.appspot.com
```
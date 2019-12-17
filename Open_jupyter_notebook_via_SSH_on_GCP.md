# Setting: Open jupyter notebook via SSH on Google Cloud Platform (GCP)

## With successful connection via ssh:
* generate default config file
`jupyter notebook --generate-config`

* Open the **config.py** with **VI**
$vi /config.py path
`vi /home/jupyter_notebook_config.py`

* Press **i** into **INSERT mode**

* Copy-paste below setting on top of the file

```
c.NotebookApp.ip = `0.0.0.0`
c.NotebookApp.open_browser = False
c.NotebookApp.port = 8888
```
* Save and leave command:
`:wq`

## Initiate ++Jupyter Notebook++

* Initiate jupyter notebook in the background (note the symbol "&")
```shell=
jupyter notebook &
```


###### ( Without background execution, jupyter notebook server will be disconnected along with terminal ssh )

* Wait for the token:
http://0.0.0.0:8888/?token=<token>

* Open with browser
`http://<google cloud machine external ip>:8888/?token=<token>`



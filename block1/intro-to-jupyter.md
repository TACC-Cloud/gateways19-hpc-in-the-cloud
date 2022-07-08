Introduction to the Jupyter Notebook Environment and generating a Tapis v3 Token
===


Jupyter is an open source project that provides a webapp interface for writing code and documents. Throughout this tutorial, we will be using a Jupyter Notebook environment for development. 

### Starting up your Jupyter Notebook Environment

If you have not already done so in the previous section, please run the following to start up your jupyter notebook
server:
```
docker run --rm -it -p 8888:8888 tapis/jupyter
```

It should have started a single container from the `tapis/jupyter` image, which prints out a url to access the jupyter
notebook from the browser. You can copy paste this url in your browser and access the jupyter notebook.

Your jupyter notebook server should now be running at `http://127.0.0.1:8888/?token=<my_token>`, where <my_token> is
from the url printed out during server startup.
You can reach your server by going to that location in a browser window.

Once you open a browser with your Jupyter environment, you should see something similar to this: 

<img src="../images/jupyter1.png" class="img-responsive" alt="Jupyter interface"> 

**Note**: You can either create a new notebook or upload the example img_classify.ipynb for this tutorial. We recommend using the existing notebook, so it will be easily to follow along.

Git clone the tutorial repo in your local computer

```
git clone https://github.com/TACC-Cloud/pearc22-portable-computing-cloud-hpc.git

```
From your Jupyter notebook, upload the img_classify.ipynb and you will be all set to work through the hands-on exercises.

**OR**

### Creating a new Notebook.

To create a new notebook for writing code, start by clicking 'New' in the upper right corner. From here, you will be able to choose what type of notebook you want. For this tutorial, we will be using Python 3. 

<img src="../images/jupyter2.png" alt="Jupyter Notebook">

Once you open a notebook, you can write and run python code. To execute a line of code, press `shift + Enter`. 



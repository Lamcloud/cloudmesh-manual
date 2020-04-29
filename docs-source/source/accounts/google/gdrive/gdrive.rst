Python Google Drive API
-----------------------

Before writing the Python interface for Google Drive, we need to setup
an email account, with that email account we will get a set of google
services and one of them is Google Drive with 15 GB overall storage.

After that we need to go through the Google Drive Quick start guide:

-  https://developers.google.com/drive/api/v3/quickstart/python

There we can see Enable API option as shown in the next picture:

.. figure:: images/image1.png
   :alt: Enable API

   Enable API

Once we enable that we will get credentials.json file where all of our
credentials are stored that can be used to communicate with our Google
Drive through Python Interface. After that, we will be redirected to a
page where we need to create our own project as shown in the next
picture:

.. figure:: images/image2.png
   :alt: Create a project

   Create a project

As we see next we need to select Google Drive API from here

.. figure:: images/image16.png
   :alt: Add credentials

   Add credentials

After that, we need to obtain the client_secret file as shown next: (The
file that is downloaded as ``client_id.json`` needs to be renamed as
``client_secret.json``)

.. figure:: images/image18.png
   :alt: Rename the file

   Rename the file

After this we need to click ``Done`` otherwise it would not set the
Google Drive API.

After this if we run Authentication.py we will be redirected to our
default browser to put our our login id and password and after that it
asks to authenticate our credentials. If we allow that as shown next:

.. figure:: images/image21.png
   :alt: Grant permissions

   Grant permissions

We will get the screen something like given next (as the authentication
pipeline has bees completed).

.. figure:: images/image23.png
   :alt: Authentication success

   Authentication success

.. todo:: Google account. This documentation is a bit unstructured and
	  repetitive. Yet errors such as references to
	  Authentication.py are conducted which does not exist.

If the authentication flow is completed then the Authentication.py will
create a ``google-drive-credentials.json`` file in ``.credentials``
folder. This file can be used for future purposes. If we delete this
file then the ``Authentication.py`` will again ask for login id and
password and again create that file automatically.

So, now with the

-  ``client_secret.json``,
-  ``google-drive-credentials.json``

we can now use

.. todo:: Google account. This documentation is a bit unstructured and
	  repetitive. Yet errors such as references to
	  Authentication.py are conducted which does not exist.

	  -  ``Authentication.py`` and ``Provider.py``

.. todo:: Google account. location of the file is missing

Once all these steps are done correctly, then we can use the Python
program interface to transfer the files between our Python program and
Google Drive.

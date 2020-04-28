Box Account
===========

Box provides a cloud file sharing service for businesses. Clients exists
for Windows, MacOS, and Linux. To obtain an account you have to first
visit the box home page as

-  https://www.box.com/home

Sign up
-------

To sign up for the account, click on the top right hand corner of the
box `homepage <https://www.box.com/home>`__ on the ``Get Started``
button.

.. figure:: images/box/get_started.png
   :alt: Get started

   Get started

From the plans page, select the ``Individual`` tab and then click on the
free option.

.. figure:: images/box/individual_plan.png
   :alt: Individual plan

   Individual plan

Fill out the required information and click ``Submit``. You will receive
a confirmation email with a link to verify your account.

.. figure:: images/box/information.png
   :alt: Ask for Information

   Ask for Information

Once you have verified your account and signed in, you will be taken to
a page that asks you about how you are using Box. You may fill this out
or click ``Skip this and go straight to Box`` below the ``Next`` button.

.. figure:: images/box/skip.png
   :alt: Next

   Next

Creating an app
---------------

Navigate to the `developer
console <https://app.box.com/developers/console>`__

-  https://app.box.com/developers/console

and select ``Create New App``. You will need to select what type of
application you are building and an authentication method for your app
and then enter an app name (you can change this later). Once your app
has been created, click View App. You will then need to click the
profile button in the top right corner of the page, and go to
``Account Settings``. Scroll down to the Authentication section and
click ``Require 2-step verification for unrecognized logins``, then
follow the prompts.

Authentication with JWT
-----------------------

In the Configuration panel of the Developer Console, scroll down to the
section titled ``Add and Manage Public Keys`` and click
``Generate a Public/Private Keypair``:

.. figure:: images/box/box_add_key.png
   :alt: Box Add Key

   Box Add Key

Once you have generated a keypair, a ``config.json`` file will
automatically download. Save this file in a secure location as you will
need it for authentication purposes. We recommend storing it at
``~/.cloudmesh/box/config.json``. This will avoid that you conflict with
another file called ``config.json``

-  [ ] todo: Box. A program is missing that adds the json key to the
   yaml file. This is the same as in Azure.

References
----------

More information about box can be found at:

-  https://developer.box.com/reference

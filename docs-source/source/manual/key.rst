key
===

.. parsed-literal::

   Usage:
     key  -h | --help
     key list --cloud=CLOUDS [--output=OUTPUT]
     key list --source=ssh [--dir=DIR] [--output=OUTPUT]
     key list --source=git [--output=OUTPUT] [--username=USERNAME]
     key list [--output=OUTPUT]
     key init
     key add NAME --filename=FILENAME [--output=OUTPUT]
     key add [NAME] [--source=FILENAME]
     key add [NAME] [--source=git]
     key add [NAME] [--source=ssh]
     key delete NAMES [--cloud=CLOUDS] [--dryrun]
     key upload [NAMES] [--cloud=CLOUDS] [--dryrun]
     key upload [NAMES] [VMS] [--dryrun]
     key group upload [NAMES] [--group=GROUPNAMES] [--cloud=CLOUDS] [--dryrun]
     key group add [NAMES] [--group=GROUPNAMES] [--cloud=CLOUDS] [--dryrun]
     key group delete [--group=GROUPNAMES] [NAMES] [--dryrun]
     key group list [--group=GROUPNAMES] [--output=OUTPUT]
     key group export --group=GROUNAMES --filename=FILENAME
     key gen (ssh | pem) [--filename=FILENAME] [--nopass] [--set_path] [--force]
     key reformat (ssh | pem) [--filename=FILENAME] [--format=FORMAT]
                              [--nopass] [--pub]
     key verify (ssh | pem) [--filename=FILENAME] [--pub] [--check_pass]

   Arguments:
     VMS        Parameterized list of virtual machines
     CLOUDS     The clouds
     NAME       The name of the key.
     SOURCE     db, ssh, all
     OUTPUT     The format of the output (table, json, yaml)
     FILENAME   The filename with full path in which the key is located
     FORMAT     Desired key format (SubjectInfo, SSH, OpenSSL, PKCS8)

   Options:
      --dir=DIR             the directory with keys [default: ~/.ssh]
      --check_pass          Flag where program query user for password
      --filename=FILENAME   the name and full path to the file
      --nopass              Flag indicating if the key has no password
      --output=OUTPUT       the format of the output [default: table]
      --pub                 Indicates that the public key is passed in
      --set_path            Sets the cloudmesh encryption key path to
                            the full path of the generated keys
      --source=SOURCE       the source for the keys
      --username=USERNAME   the source for the keys [default: none]


   Description:

       Please note that some values are read from the cloudmesh.yaml
       file. One such value is cloudmesh.profile.user

       Management of public keys is an essential component of accessing
       virtual machines in the cloud. There are a number of sources
       where you can find public keys. This includes the ~/.ssh
       directory and for example github. If you do not already have a
       public-private key pair they can be generated using cloudmesh

       key gen ssh 
           This will create the public-private keypair of ~/.ssh/id_rsa
           and ~/.ssh/id_rsa.pub in OpenSSH format

       key gen pem 
           This will create the public-private keypair of ~/.ssh/id_rsa
           and ~/.ssh/id_rsa.pub in PEM format

       key gen (ssh | pem) --filename=~/.cloudmesh/foobar
           This will generate the public-private key pair of 
           ~/.cloudmesh/foobar and ~/.cloudmesh/foobar.pub

       key gen (ssh | pem) --filename=~/.cloudmesh/foobar --set_path
           This will generate the keys as stated above, but it will
           also set cloudmesh to use these keys for encryption.

       Keys can also be verified for their formatting and passwords.
       By default cloudmesh checks ~/.ssh/id_rsa and ~/.ssh/id_rsa.pub
       If the key is password protected the formatting can only be
       verified if the password is provided (--check_pass argument)

       key verify pem
           Verifies that ~/.ssh/id_rsa has PEM format

       key verify ssh --pub
           Verifies that ~/.ssh/id_rsa.pub has OpenSSH format

       key verify pem --filename=~/.cloudmesh/foobar
           Verifies if the private key located at ~/.cloudmesh/foobar
           is password protected

       key verify pem --filenam=~/.cloudmesh/foobar --check_pass
           Request the password to the file, then checks if the
           key is in proper PEM format

       You may find the need to keep the values of your keys but
       different encodings or formats. These aspects of your key can
       also be changed using cloudmesh.

       key reformat pem
           Will reformat the ~/.id_rsa.pub key from PEM to OpenSSH

       key reformat ssh
           Will reformat the ~/.id_rsa.pub key from OpenSSH to PEM

       key reformat --filename=~/.id_rsa --format=PKCS8
           Will reformat the private key to PKCS8 format

       Keys will be uploaded into cloudmesh database with the add
       command under the given NAME. If the name is not specified the name
       cloudmesh.profile.user is assumed.

        key add NAME  --source=ssh
            adds the default key in ~/.ssh/id_rsa.pub
        key add NAME  --source=FILENAME
            adds the key specified by the filename with the given name
        key add NAME --git --username=username
            adds a named github key from a user with the given github
            username.

        key set
            adds the ~/.ssh/id_rsa.pub key with the name specified in
            cloudmesh.profile.user.
            It also sets the variable key to that user.


       Once the keys are uploaded to github, they can be listed
       To list these keys the following list functions are provided.

        key list --source=git  [--username=USERNAME]
            lists all keys in git for the specified user. If the
            name is not specified it is read from cloudmesh.yaml
        key list --source=ssh  [--dir=DIR] [--output=OUTPUT]
            lists all keys in the directory. If the directory is not
            specified the default will be ~/.ssh

        key list NAMES
            lists all keys in the named virtual machines.


        List command can use the [--output=OUTPUT] option

            list the keys loaded to cloudmesh in the given format:
            json, yaml, table. table is default. The NAME can be
            specified and if omitted the name cloudmesh.profile.user
            is assumed.

        To get keys from the cloudmesh database the following commands
        are available:

        key delete NAMES
            deletes the Named keys. This may also have an impact on groups
        key rename NAME NEW
            renames the key from NAME to NEW in the cloudmesh database.

       Group management of keys is an important concept in cloudmesh,
       allowing multiple users to be added to virtual machines while
       managing the keys associated with them. The keys must be uploaded
       to cloudmesh database with a name so they can be used in a
       group. The --dryrun option executes the command without
       uploading the information to the clouds. If no group name is
       specified the group name default is assumed. If no cloudnamesh
       are specified, all active clouds are assumed. active clouds
       can be set in the cloudmesh.yaml file.

        key group delete [GROUPNAMES] [NAMES] [--dryrun]
            deletes the named keys from the named groups.

        key group list [GROUPNAMES] [--output=OUTPUT]
            list the key names and details in the group.

        key group upload [GROUPNAMES] [CLOUDS] [--dryrun]
            uploads the named groups to the specified clouds.

       In some cases you may want to store the public keys in files. For
       this reason we support the following commands.

        key group add --group=GROUPNAME --file=FILENAME
            the command adds the keys to the given group. The keys are
            written in the files in yaml format.


        key group export --group=GROUNAMES --filename=FILENAME
            the command exports the keys to the given group. The keys are
            written in the files in yaml format.


        The yaml format is as follows:

        cloudmesh:
          keys:
            NAMEOFKEY:
              name: NAMEOFKEY
              key: ssh-rsa AAAA..... comment
              group:
              - GROUPNAME
            ...

        If a key is included in multiple groups they will be added
        to the grouplist of the key

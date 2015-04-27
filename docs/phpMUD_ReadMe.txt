phpMUD Codebase Documentation

I. The Code

The code currently works in layers, as do most MUDs out there. That is, the 'character'
is the top most layer in most instances, and it interacts with the lower socket layer through
some sort of connection or descriptor layer.

The Socket class should never be interfaced with by the Player class. The Player class has
several means it can use by interfacing through the Connection class. Any other class that
a player might find themselves in (accounts, ect) should do the same. That is, interface through
the Connection class.

The Database Class provides universal support for accessing the database backbone. This means
that if you were to require a database other than MySQL, you could simply rewrite the class
to work with your database needs. All database commands (such as mysql_num_rows) should not be
called unless from within this class. The Database class also provides universal functions for
saving an object to a table. In order to make use of this, the object must meet the following
critera:

1) Have it's class and save-to table defined in $table_data, atop the database.class file.
2) Have all fields that will be saved to the database marked as PUBLIC.
3) Have fields in the database that 
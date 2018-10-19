# exileDB

exileDB is a simple JSON document database written in PHP.

# Examples
# Open Database
<?php
	require 'exileDB.php';

	$db = new exileDB()-open("db.exile");
?>
Output in db.exile
-----------------------------------------------------------------------------------------
{"name":"db\r\n","tables":{},"data":{}}

# Create Table
<?php
	require 'exileDB.php';

	$db = new exileDB()-open("db.exile");
	$db->createTable('{"name": "tblusers", "cols": ["name", "age", "gender"]}');
?>
Output in db.exile
-----------------------------------------------------------------------------------------
{"name":"db\n\n","tables":{"tblusers":["_id","name","age","gender","created_at","updated_at"]},"data":{"tblusers":[]}}

# Drop Table
<?php
	require 'exileDB.php';

	$db = new exileDB()-open("db.exile");
	$db->dropTable("tblusers");
?>
Output in db.exile
-----------------------------------------------------------------------------------------
{"name":"db\r\n","tables":{},"data":{}}

# Select Table
<?php
	require 'exileDB.php';

	$db = new exileDB()-open("db.exile");
	$db->setTable("`tblusers");
?>

# Insert Data
<?php
	require 'exileDB.php';

	$db = new exileDB()-open("db.exile");
	$db
		->setTable("`tblusers")
		->insert('{"name": "Frank Galos", "age": "1000", "gender": "Male"}');
?>
Output in db.exile
-----------------------------------------------------------------------------------------
{"name":"db\r\n","tables":{"tblusers":["_id","name","age", "gender", "created_at","updated_at"]},"data":{"tblusers":[{"_id": "53f934f03333340880001e9b","name": "Frank Galos","age": "100","gender": "Male","created_at":"2018-05-12 2:42:24","updated_at":"2018-05-12 3:22:48"}]}}

# Select Data
<?php
	require 'exileDB.php';

	$db = new exileDB()-open("db.exile");
	$db->setTable("tblusers");
	
	$data = $db->select('{"name": "Frank Galos", "age": "1000"}');
	var_dump($data);
?>
Output in browser
-----------------------------------------------------------------------------------------
array (size=1)
  0 =>
    object(stdClass)[2]
      public '_id' => string '53f934f03333340880001e9b' (length=24)
      public 'name' => string 'Frank Galos' (length=12)
      public 'age' => string '100' (length=3)
      public 'created_at' => string '2018-05-12 1:42:24' (length=18)
      public 'updated_at' => string '2018-05-12 3:22:48' (length=18)

# Update Data
<?php
	require 'exileDB.php';

	$db = new exileDB()-open("db.exile");
	$db
		->setTable("`tblusers")
		->update('{"where": {"_id": "53f934f03333340880001e9b"}, "set": {"age": "200"}}');
?>
Output in db.exile
-----------------------------------------------------------------------------------------
{"name":"db\r\n","tables":{"tblusers":["_id","name","age", "gender", "created_at","updated_at"]},"data":{"tblusers":[{"_id": "53f934f03333340880001e9b","name": "Frank Galos","age": "200","gender": "Male","created_at":"2018-05-12 9:42:24","updated_at":"2018-05-12 5:22:48"}]}}

# Delete Data
<?php
	require 'exileDB.php';

	$db = new exileDB()-open("db.exile");
	$db
		->setTable("`tblusers")
		->delete('{"name": "Frank Galos"}');
?>
Output in db.exile
-----------------------------------------------------------------------------------------
{"name":"db\r\n","tables":{"tblusers":["_id","name","age", "gender", "created_at","updated_at"]},"data":{"tblusers":[]}}

<br><br>

# CLIENTS USING THIS DATABASE INCLUDE
<br>
This are clients that found this DB worth trying.
<br><br>
<a href="https://flights.karibuworld.com/">Karibu World - Safari Africa and Travel Your World</a><br>
<a href="https://neditor.herokuapp.com/">Neditor</a>


<br><br><br>

* MIT License

* Copyright (c) 2018 Frank Galos

* Permission is hereby granted, free of charge, to any person obtaining a copy
* of this software and associated documentation files (the "Software"), to deal
* in the Software without restriction, including without limitation the rights
* to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
* copies of the Software, and to permit persons to whom the Software is
* furnished to do so, subject to the following conditions:

* The above copyright notice and this permission notice shall be included in all
* copies or substantial portions of the Software.

* THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
* IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
* FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
* AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
* LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
* OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
* SOFTWARE.



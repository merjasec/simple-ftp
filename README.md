simple-ftp
==========

Simple wrapper for PHP (http://php.net/manual/en/book.ftp.php) FTP

Motivation for this class was to simplify usage of FTP
so instead of doing:

<pre>
$conn = ftp_connect($host, $port, $timeout);
if ($conn) {
  $login_result = ftp_login($conn, $user, $password);
  if ($login_result) {
          $connected = TRUE;
  }
}
</pre>

We simply do

<pre>
$ftp = new SimpleFtp($host, $port, $user, $password);
$ftp->connect();
</pre>

In addition we can use shell commands like:

cd  -change dir
put -upload a file
ls - list directory
get - download file


Example:

<pre>

$options = array;
$options['server'] = 'ftp.example.com';
$options['port'] = 21;
$options['user'] = 'user';
$options['pass'] = 'password';

//connect to server
$ftp = new SimpleFtp($options);
$ftp->connect();
//got to folder
$ftp->cd('Folder1');
//upload file
$ftp->put('file1.zip');
//list content
$ftp->ls();
//end session
$ftp->disconnect();
</pre>

TODO:

- add multiple file/folder upload
- add upload/download progress display
- fix code comments
- ...


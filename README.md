# Codeigniter XMLRPC - HTTPS extension
With a little trick, you can use your Codeigniter XML-RPC server with SSL (HTTPS) since this function has no implemented officially.
If you use Codeigniter's one of the older versions, you may be happy after you figure out, your "old" XML-RPC server can work again via HTTPS.
If something is old, it doesn't mean, it's useless.

## How to install?
- Download the source file (`Xmlrpc.php`) and overwrite the old one in your `[CODEIGNITER]/system/libraries` folder
- Try it and use, because your XML-RPC server/client will work again via SSH/HTTPS

## What is the trick?
It's very simple, just added an extension to this line:

`$fp = @fsockopen($this->server, $this->port,$this->errno, $this->errstr, $this->timeout);`

... and now looks like this:

`$fp = @fsockopen(($this->port == 443 ? "ssl://" : "").$this->server, $this->port,$this->errno, $this->errstr, $this->timeout);`

# Codeigniter-Migrations

## Contributors

* [Phil Sturgeon](http://philsturgeon.co.uk)
* [webPragmatist](http://www.webPragmatist.com)
* [Spicer Matthews, Cloudmanic Labs, LLC](http://www.cloudmanic.com)

### Based On

[Migrations](http://codeigniter.com/wiki/Migrations/) by Mat'as Montes
	
## About

An open source utility for Codeigniter inspired by Ruby on Rails.

The one thing Ruby on Rails has that Codeigniter does not have built in
is database migrations. That function to keep track of database changes (versions)
and migrate your database to what ever version you need. Migrate up or migrate down.
With this library you can now do this.

## Install

Copy the files to these locations.
	
    config/migrations.php -> application/config/
    libraries/Migrations.php -> application/libraries/
    controllers/migrate.php -> application/controllers/

The migration files included in this are just examples. You should install them where ever you 
point your `$config["migrations_path"]` to.
 
## Usage
	
    $this->load->library('migrations');
    $this->migrations->set_verbose(TRUE); // echo statements or not
    $this->migrations->version(id); // migrate the database to a particular version
    $this->migrations->latest(); // migrate the database to the latest version
    $this->migrations->install(); // install to the latest version.

The migrate.php controller just shows the use of these functions. If you are going to use it.
comment out the `show_error()` in the construct, and put it back in place when you are done.
	
## Examples
	
### Make sure our database is up-to-date

    if ( ! $this->migration->latest())
    {
    	show_error($this->migration->error);
    }
	
### Update (or come back to) migration 5

    if ( ! $this->migration->version(5))
    {
    	show_error($this->migration->error);
    }

## Other Helpful Stuff

Included in this git repo is an example CodeIgniter Hook and a basic application/config/hooks.php to show
how to enable it. This hook is one of several ways to have migrations run on every page load. You
could also place the code into a MY_Controller.

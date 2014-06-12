liferaybase
===========

Use Vagrant+Chef to initialize Liferay

## Requirements
* Ruby
* Vagrant
* Chef

## Installation
1. Clone this repo `git clone git@github.com:xhawk/liferaybase`
2. Install Vagrant
3. Install Chef `curl -L https://www.opscode.com/chef/install.sh | sudo bash`
4. Run `libarian-chef install` to download the cookbooks
5. Run `vagrant up`
6. Goto localhost:8080 with your browser
7. Select other database than default hypersocnic database
8. Use `liferay_user` as PostgreSQL user and `l1f3r4y$` as a password
9. Fill the forms that wizard presents
10. ???
11. Profit
		

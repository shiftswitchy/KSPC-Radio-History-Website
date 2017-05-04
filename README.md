# Project Name

TODO: Write a project description

## Installation

TODO: Describe the installation process

## Usage

TODO: Write usage instructions

## Contributing

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request :D

## History

TODO: Write history

## Credits

TODO: Write credits

## License

TODO: Write license



# README

### kspc.org
Migrating to Ruby on Rails

# Changelog

### Tina, 4/17 - Dynamic Home Page, also it's hosted on the remote server (Heroku)! See here:

Changes:
execjs was causing compilation errors when deploying on Heroku. A quick fix (by disabling the uglifier) in production.rb was used.
program schedule URL has to be https:/ or it will not work. 

https://kspcdev.herokuapp.com/
Here's how to push your own changes onto the server (currently.) Eventually we'd want to make an account for Erica or Luke.

You can follow this tutorial: https://devcenter.heroku.com/articles/getting-started-with-rails4
The commands you need are: you install (brew install heroku) then you login (heroku login) with my credentials (tzhu@g.hmc.edu, password: message me on facebook for it). Then, you can run (heroku create) in the KSPC folder. Then we run (git push heroku master) to push
to heroku's remote server. Also, since we used mySQL you might need to do the commands:  https://devcenter.heroku.com/articles/cleardb under "Provisioning the add-on" to config it to use the ClearDb mySQL add-on.
Then, do (heroku run:detached rake db:migrate) see here: http://stackoverflow.com/questions/17237809/heroku-run-rake-dbmigrate-command-error . It should work then.
Note: Please alert others to be sure of your changes before pushing to remote server just in case.  

### Cha, 4/12 - Wordpress Migration
Please do the following to migate all blogs from wordpress
1. Run 'rake wordpress:import' When it works it will print a lot of stuff (all the contents) and migrate it to blogs.
2. The images are too large to put on github, so I put in on Google drive link: https://drive.google.com/open?id=0B8CcBOaEIxGHZjNKc210eU1yalU
Put this folder in 'public/' Most pictures are in this folder, but some old ones use pic hosting service and may or may not be expired.


### Judy, 3/25 - Blog & contact/email page controller
Blog editing, updating, deleting implemented. Formatting and Disqus comment feature finished for individual blog showings. Later, the blog front page will look nice too. Admin under kspc.auto@gmail.com can monitor comments.
![screen shot 2017-03-25 at 4 13 07 pm](https://cloud.githubusercontent.com/assets/5604374/24326872/f5ef4f10-1175-11e7-8246-b8cf4f097362.png)

I've also added functionality and content editing to the contact page. All messages will go to kspc.auto@gmail.com as Cha set up.

Lastly, I made TODO notes for the homepage and formatted the subscriber form to be consistent with our bootstrap theme.

### Cha, 3/19 - Sending emails after signing up
In the homepage the subscription email will be sent when someone signups.
The sender email is kspc.auto@gmail.com and can be changed to any appropriate ones.
The content is blank but we can change it to what the client prefers.

Sometimes you could get the "already exists database", which means we have to delete the old ones. This can be done by "rails c" and drop the table (can do this from mySql as well).

### Gus, 3/6 - Added admin account
The archives page needed an admin account to create new archives, so I created one that should work site wide. To log in, visit localhost:3000/admin and enter the credentials (message me for email/pass).

I made sure to disable registration so people can't create new admin accounts. I think the assumption is that there will be just one admin account shared between the people at KSPC.

Only thing that's a little off is that the real URL for the admin page is /mains/admin. Ideally we could find a way to get rid of that mains prefix everywhere. This is fine, but it means if you go to localhost:3000/admin it won't highlight the proper tab you are on. Also added a TODO to move the admin nav buttons to the right to separate them from the rest.

### Judy, 3/6 - Made content editable
The About and Expo pages contain general info, but we do not want that info to be static. Now you can use a rich text editor (tinymce used by Evernote, LinkedIn, WordPress, and more) to edit the content through our front-end. Admin privileges will be added later.
![screen 3/5](https://cloud.githubusercontent.com/assets/5604374/23595793/8c201926-01d9-11e7-8c11-b9ab6fd9d82a.png)

Read Cha's update for solving errors. My change on master reverted #2 to work for mac. Windows developers need to change it back.

### Cha, 3/5 - Add contact page and fix homepage
Fix homepage to work with bootstrap 4 format, and create new database for contact page.

Changes that may cause errors

1. 'secrets.yml' is not pushed (in gitignore) so if the error about 'secretkey in development ... missing' please add the file back in the local repo.

2. In 'database.yml' some of us have different socket path to mysql. I've seen that it will be one of the two '/var/run/mysqld/mysqld.sock' or '/tmp/mysql.sock' please change them accordingly if you get an error about 'socket path <PATHNAME> ... not found'. Also please don't set
password in mysql, but if it has been set change it back to empty string.

3. 'rake db:migrate' or 'rake db:create' may need to be run if there is an error like 'database <DATABASE_NAME> not found'.

### Gus, 2/25 - Created archive controller/model
The archive page now has it's own controller for the CSS, html, etc. It can now be developed somewhat independently of the rest of the page. To accompany this new controller, I also created a new model (like a class) for an archive. This model has a title field and a file attachment via PaperClip. Currently it just supports images, but other file types can be added via archive.rb. Most of the code for the archive page currently resides in archives/new.html.erb, archives/index.html.erb, archive.rb, and archives_controller.rb

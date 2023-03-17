I would like to explain now about the web application I created for the final project of CS50, "PRO! Simply put, this web application is a programming sns that tweets about what you have studied. The name of the application, "PRO!", means "to record the process of studying programming in order to become a professional in the field".
I did my development using AWS cloud9, but to develop in a local environment you must first
init.sh(参考)
# pyenv configuration
git clone https://github.com/pyenv/pyenv ~/.pyenv
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bash_profile
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bash_profile
echo 'eval "$(pyenv init -)"' >> ~/.bash_profile
source ~/.bash_profile
pyenv install 3.7.9
git clone https://github.com/pyenv/pyenv-virtualenv.git ~/.pyenv/plugins/pyenv-virtualenv
echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.bash_profile
source ~/.bash_profile
pyenv virtualenv 3.7.9 part3
pyenv global part3

# pip install
pip install -r requirements.txt

# SQLite3 update
cd ~/
wget https://www.sqlite.org/2020/sqlite-autoconf-3330000.tar.gz
tar zxvf sqlite-autoconf-3330000.tar.gz
cd ~/sqlite-autoconf-3330000
./configure
make
sudo make install
sudo mv /usr/bin/sqlite3 /usr/bin/sqlite3_old
sudo ln -s /usr/local/bin/sqlite3 /usr/bin/sqlite3
echo 'export LD_LIBRARY_PATH="/usr/local/lib"' >> ~/.bash_profile
source ~/.bash_profile
cd ~/environment
exec $SHELL -l

and note that $sh init.sh must be run on the terminal. This shell script will also install the libraries listed in requirements.txt.
Now, let's move on to the explanation of the contents. First of all, you need to register as a user to use "PRO! The user registration requires the following items
・E-mail address
・User Name
・Password
There are three types of passwords. If the password is too simple, such as less than 8 characters or "123456789," or if it is very similar to the user name, the user will be warned to set a different password and will not be able to register.
After the user has registered, the login screen will appear. The login screen asks for an email address and password. Of course, if the user is not registered, or if the e-mail address and password are incorrect, the user will not be able to log in.
Once logged in, the user will be taken to the timeline screen. On the timeline screen, you can tweet about what you have learned with images, or view a list of what you have tweeted so far. You can also go to the profile registration screen from the timeline screen and log out. In the profile page, you can change your user name, add a brief self-introductory sentence, and register an image.
Other features we would like to implement in the future include a function that allows users to follow other users and to view a list of tweets of people they follow on the timeline.

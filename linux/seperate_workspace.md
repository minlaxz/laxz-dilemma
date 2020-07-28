I have Ubuntu 18.04 on my laptop and I want to have completely separate workspaces on it.

Now my workspaces are sharing the icons on the dock, and when I click on icons of application that have instance in the the other workspace, it's taking me back to the workspace with the instance. I want it to open new instance in the current work space, and I don't want any indication that the other workspace is running another instance of this application.

How can I achieve that?

What solved my problem:

gsettings set org.gnome.shell.app-switcher current-workspace-only true
gsettings set org.gnome.shell.extensions.dash-to-dock isolate-workspaces true


[detail](https://askubuntu.com/q/1068097/944917)

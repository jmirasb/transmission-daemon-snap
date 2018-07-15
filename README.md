# Snappy Transmission-daemon

Transmission is a cross-platform BitTorrent client, this snap contains daemon client to use it in ubuntu core or server.
For more information you can visit official Transmission's homepage <https://transmissionbt.com/>

## Install

For now the snap is under development so is not available in the store yet. You can download git code and create the snap using snapcraft:

     $ git clone https://github.com/jmirasb/transmission-daemon-snap.git
     $ cd transmission-daemon-snap
     $ snapcraft
     
or download directly the snap in release section and install using snap:
     
     $ sudo snap install <snap> --dangerous

## Configure

The snap use snappy get/set configuration system, so you can use:

      $ snap get transmission-daemon-backend
      
to see the available configuration keys and values, and:

      $ snap set transmission-daemon-backend <key>=<value>

to configure it. Remember stop server before change any configuration parameter because the server overwrite configuration file when stops:

      $ sudo systemctl stop snap.transmission-daemon-backend.transmission-daemon.service

#### To make the web server accessible without configuration when it's installed, all security parameters are deactivated in default configuration file. So, is recommended reconfigure server and activate IP filter or user/password authentication, for instance:
     
     $ snap set transmission-daemon-backend rpc-whitelist-enabled=true rpc-whitelist="127.0.0.1;1.0.0.*"

   ### Removable media

The interface providing the ability to access removable media directory is not automatically connected upon install, so if you'd like to use it in the config file for download/watch/incomplete directories, you need to give the snap permission to access removable media by connecting that interface:

    $ sudo snap connect transmission-daemon-backend:removable-media

## Issues

Please report the snap issues to project issues section.


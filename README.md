# gitlab-irc

Tiny Sinatra App that takes POST Calls from Gitlab Web Hooks and pushes them in your IRC Channel of choice.

    22:59 < GitLabBot> New Commits for 'repo-name'
    22:59 < GitLabBot> by Aleks | Got shit done | http://yourgitlabhost.com/repo-name/commits/f9cbbe01c....
    22:59 < GitLabBot> by Aleks | Got even more shit done | http://yourgitlabhost.com/repo-name/commits/f9cbbe01c....

### Install Sinatra

<code>
gem install sinatra
</code>

### Configure
Set IRC settings in gitlab-irc.rb

    # IRC Config
    IRC_HOST = 'irc.freenode.org'
    IRC_PORT = 6667
    IRC_CHANNEL = '#yourchannel'
    IRC_NICK = 'GitLabBot'
    IRC_REALNAME = 'GitLabBot'

### Launch
    ruby gitlab-irc.rb

You should see output like this:

    » ruby gitlab-irc.rb  
    == Sinatra/1.3.3 has taken the stage on 4567 for development with backup from Thin
    >> Thin web server (v1.4.1 codename Chromeo)
    >> Maximum connections set to 1024
    >> Listening on 0.0.0.0:4567, CTRL+C to stop

### Enable Web Hook Support in your GitLab Repository

Every Gitlab repository can have individual Web Hooks. Copy your gitlab-irc address <code>http://xxx.xxx.xxx.xxx:4567/commit</code> and set it for every Repository that should send notifications to your IRC channel.

### Run in Background

To keep gitlab-irc running, you should start it in some kind of background task. A good choice would be <code>tmux</code> or <code>screen</code>.

If you want to configure the webserver port, take a look at the [Sinatra Documentation](http://www.sinatrarb.com/configuration.html). You can also run it like any other Sinatra app.
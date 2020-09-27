# Splunk_TA_Truvis_Linux_History

This uses the older history style for monitoring commands. For the newer and better way use AduitD. 

Till the TA gets released, this needs to be added to the master .bashrc generally under /etc/profile.d

```
PROMPT_COMMAND='history -a'
export HISTCONTROL=
if [ -f /etc/bashrc ]; then
        . /etc/bashrc
fi
    PROMPT_COMMAND="${PROMPT_COMMAND:+$PROMPT_COMMAND ; }"'echo -e $$\\t$USER\\t$SSH_CONNECTION\\t$HOSTNAME\\tscreen $WINDOW\\t`date +%D%t%T%t%Y%t%s`\\t$PWD"$(history 1)" >> ~/.bash_eternal_history'
    [ "$PS1" = "\\s-\\v\\\$ " ] && PS1="[\u \w]\\$ "
    if [ "x$SHLVL" != "x1" ]; then # We're not a login shell
        for i in /etc/profile.d/*.sh; do
      if [ -r "$i" ]; then
          . $i
      fi
  done
    fi
shopt -s histappend
```

In Splunk you can create your own expression or use this one for being able to search the content.

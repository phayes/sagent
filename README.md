# sagent
Generate an re-usable ssh-agent for ssh key forwarding

This is a small script to generate a reusable ssh-agent for use with ssh key forwarding

The classic use-case is to do git pull on a remote server without sending your ssh keys

```bash
export SSH_AUTH_SOCK="$(sagent)"
ssh -A remoteserver.com
git pull
```

It will helpfully re-use any existing ssh-agent processes, so you dont need to worry about spawning too many. It will only ever spawn a new ssh-agent process if needed.

This script can be called in one of two ways:
`export SSH_AUTH_SOCK="$(sagent)"`
`source /path/to/sagent`

Best is to put it in your bash profile so that an agent will always be ready to go when you need it
`echo 'export SSH_AUTH_SOCK="$(sagent)"' > ~/.bashrc`

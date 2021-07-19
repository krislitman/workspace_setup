# Git Instructions
<hr>

1. Install Git from the command line with homebrew:
`brew install git`
<br>

2. Configure Git:
```
git config --global user.name "Kris Litman"
git config --global user.email kris.d.litman@gmail.com
git config --global init.defaultBranch main
git config --global core.editor "code --wait"
git config --global pull.rebase false
```
3. Generate SSH key:
```
ssh-keygen -t rsa -C "kris.d.litman@gmail.com"
```
>When prompted to enter a file to save the key,
>press Enter. Saves to default location. ~/ssh/id_rsa
>Press enter when asked for password
>("Means 'no password'")

4. Add the SSH key to Github:
`ssh-add ~/.ssh/id_rsa`
<br>

5. Copy the key to clipboard:
`pbcopy < ~/.ssh/id_rsa.pub`

6.Go to GitHub: https://github.com/settings/keys

>Click New SSH key button
>Leave title empty
>Paste key into section with command + v
>Hit Add SSH key button

7. Check that it worked with the command:
`ssh -T git@github.com`
If prompeted to continue connecting, type `yes`

If you see this message, it means everything was successful:
`Hi ! You've successfully authenticated, but GitHub does not provide shell access.`

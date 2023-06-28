# Multiple github account
## Configuration for multiple github account

### Step 1
- Create SSH keys for all accounts
- First make sure your current directory is your .ssh folder.
- Syntax for generating unique ssh key for an account is:

```bash
ssh-keygen -t ed25519 -C "your-email-address"
```

- A message will appear:
Generating public/private ed25519 key pair.
Enter file in which to save the key `(C:\Users\ACER/.ssh/id_ed25519):`

```bash
C:\Users\ACER\.ssh\id_ed25519_<unique_filename>
```

- Add the above path with your unique and press enter key



### Step 2
- Add SSH public key to the Github
- For the next step we need to add our public key (that we have generated in our previous step) and add it to corresponding github accounts.

### Step 3

-Create a Config File and Make Host Entries, the `~/.ssh/config` file allows us specify many config options for SSH.

- If config file not already exists then create one (make sure you are in ~/.ssh directory)

- Now we need to add these lines to the file, each block corresponding to each account we created earlier.

``` bash
#rahul-office account
Host github.com-rahul-office
    HostName github.com
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/github-rahul-office

#rahul-personal account
Host github.com-rahul-personal
    HostName github.com
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/github-rahul-personal
```


### Step 4

- Cloning GitHub repositories using different accounts
- So we are done with our setups and now its time to see it in action. We will clone a repository using one of the account we have added.

- Make a new project folder where you want to clone your repository and go to that directory from your terminal.

- For Example: I am making a repository on my personal github account and naming it TestRepo Now for cloning the repo use the below command:

```bash

git clone git@github.com-{your-username}:{owner-user-name}/{the-repo-name}.git

[e.g.] git clone git@github.com-rahul-personal:rahul-personal/TestRepo.git

```


### Step 5

From now on, to ensure that our commits and pushes from each repository on the system uses the correct GitHub user — we will have to configure user.email and user.name in every repository freshly cloned or existing before.

- To do this use the following commands.

```bash
git config user.email "my_office_email@gmail.com"
git config user.name "Rahul Pandey"

git config user.email "my-personal-email@gmail.com"
git config user.name "Rahul Pandey"
```
     
- Pick the correct pair for your repository accordingly.

- To push or pull to the correct account we need to add the remote origin to the project
```bash
git remote add origin git@github.com-rahul-personal:rahul-personal

git remote add origin git@github.com-rahul-office:rahul-office
```
     
Now you can use:

```bash
git push
     
git pull
```
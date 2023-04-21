# includeIf_for_conditional_config

After git 2.13, it adds a feature that can include other config file in .gitconfig. Now I need multiple gitconfig for different git user/repo.

## References

1. The doc of `git-config` on git-scm.com:
<https://git-scm.com/docs/git-config#_conditional_includes>

2. Stack Overflow question "Is it possible to configure user.name and user.email per wildcard domains in .gitconfig?"
<https://stackoverflow.com/questions/13750953/is-it-possible-to-configure-user-name-and-user-email-per-wildcard-domains-in-gi>

## Operations

The old `.gitconfig` is single file in `~`, and it must have `user.name`, `user.email`.
Now, I move config in `user` like above to multiple files.

1. In the main .gitconfig location at `~/.gitconfig`, add these:

    ```.gitconfig
    ; includeIf the {username} url:
    [includeIf "hasconfig:remote.*.url:git@github.com:{username}/**"]
	    path = %(prefix)/D:/{some}/{path}/{to}/{filename}.gitconfig
    ```

2. In the includeIf .gitconfig located at as the `~/.gitconfig` wrote, add these:

    ```{filename}.gitconfig
    ; specified the {username}'s config:
    [user]
        name = {username}
        email = {email}
    
    ; config Git to use SSH to sign commits and tags:
    [user]
        signingkey = ~/.ssh/{path}/{ssh_public_key}.pub
    
    ; ssh authentication key:
    [core]
	    sshCommand = "ssh -i ~{specified_user}/{path}/{to}/{private_key}"
    ```

3. test it:

    ```bash
    cd {git repo path}
    ssh -Tv git@github.com
    {should print public key pass phrase}
    {some ssh output log}
    git init
    echo "# title" >> README.md
    git add .
    git commit -m "test" -S
    {should print public key pass phrase}
    git remote add {url}
    git branch -M master
    git push -u origin master --dry-run
    {should print public key pass phrase}
    ```

it works.

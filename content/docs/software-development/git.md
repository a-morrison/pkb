---
title: "Git"
---
# Git
Version Control[^1]

## GitFlow
Simple but powerful workflow for stucturing complex git repos[^2].

EX:
{{< mermaid >}}
gitGraph:
options
{
    "nodeSpacing": 70,
    "nodeRadius": 10
}
end
commit
branch releases
branch develop
branch feature
checkout releases
commit
checkout develop
commit
checkout feature
commit
checkout develop
commit
checkout releases
commit
checkout feature
commit
commit
checkout develop
merge feature
checkout releases
merge develop
checkout master
merge releases
{{< /mermaid >}}

## Environment Based Branch Model
{{< hint info >}}
This could be an effective git model for GovGrants.
{{< /hint >}}
Applicable when each branch should represent an environment (Prod, QA, Dev, etc)[^3].

Rules:

- Don't commit directly to an envrionment branch
- Don't merge one environment branch into another
- Feature branches should be based on master and envrionment agnostic

## Git-Crypt
`git-crypt` allows for encrypting files in a git repo. It's easy to install on
linux distros but Windows can be a pain. This will go over how to do so on 
Windows due to its absurdidty.

First you'll need GPG. This can be installed from via an exe from GNU at 
https://gnupg.org/download/
Once it is installed you need to create a key pair. Do this by running the following
commands:
1. `gpg --full-generate-key`
2. Select default `RSA and RSA`.
3. Enter max size of `4096`
4. Take default expiration time
5. Enter user id info

Now you should have a gpg key pair. Next you'll need to export both public and
private keypairs in order to use them in the WSL. Because `git-crypt` is not
really supported on Windows we have to install it and run it via the WSL.

To export the keypairs run the following commands:
1. `gpg -o public.txt --armor --export 'key name'`
2. `gpg -o private.txt --armor --export-secret-keys 'key name'`

Using this format ensures that the keys are exported in such a way that the WSL
will recognize the key. If not then you could get a key not found error.

Next open a WSL shell and import the keypair via this command: 
`gpg --import 'file name'`.

Next update the trust status of the key by running `gpg --edit-key key_name`.
You will now see a shell for gpg with a prompt like `gpg>`. Enter the `trust`
command and update the trust level to at least a `3`. I picked a `5` originally.

Next install `git-crypt` on the WSL via `sudo apt-get install git-crypt`.

Now in your repo initalize a `git-crypt` repo as found in the 
[docs](https://github.com/AGWA/git-crypt). Your files should now be encrypted!

## Further Reference
[^1]: [Documentation](https://git-scm.com/docs)
[^2]: https://nvie.com/posts/a-successful-git-branching-model/
[^3]: https://www.wearefine.com/mingle/env-branching-with-git/
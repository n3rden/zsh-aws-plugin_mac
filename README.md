# oh-my-zsh-aws-plugin

## Pre-reqs
1) Have Oh-My-Zsh installed and configured. Ideally with Powerlevel9k (or 10k) installed and configured
2) Install the gnu versions of stuff as the mac ports are garbage:  gdate, gawk, ggrep and gsed. Brew should do this for you with the following:
        
        brew install coreutils gawk grep gnu-sed

## Setup
1) Clone this repository somewhere
2) Symlink the zsh-aws-plugin.zsh (you will need to update the path in the snippit below)

        cd <path-to-repo>/
        mkdir ~/.oh-my-zsh/plugins/zsh-aws
        ln -s <path-to-repo>/zsh-aws.plugin.zsh ~/.oh-my-zsh/plugins/zsh-aws/zsh-aws.plugin.zsh


3) Edit ~/.p10k.zsh and update the 'typeset -g POWERLEVEL9K_LEFT_PROMPT_ELEMENTS' section to look like this

          # The list of segments shown on the left. Fill it with the most important segments.
          typeset -g POWERLEVEL9K_LEFT_PROMPT_ELEMENTS=(
            > EXISTING_CONFIG
            aws_prompt_info         # AWS Prompt info from plugin
            > MORE_EXISTING_CONFIG
          )


4) Restart your terminal session

## Basic Usage

        aws_set_creds <profile name as per the awscli tool>   # Sets the current AWS provile in the terminal session

        aws_auth_mfa             # Authenticates your MFA terminal session
        aws_persist_mfa          # Dump the temporary MFA session credentials to the .aws/credentials file. Good for stuff like 

  
The 'aws_persist_mfa' command was added spcifically so I could use Cyberduck [which needs this profile](https://svn.cyberduck.io/trunk/profiles/S3%20(Credentials%20from%20AWS%20Security%20Token%20Service).cyberduckprofile)


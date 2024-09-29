--------------To change the root password in gitlab enterprise-----------
docker exec -it gitlab-runner-gitlab-1 gitlab-rails runner "user = User.find_by(username: 'root'); user.password = 'anish123'; user.password_confirmation = 'anish123'; user.save!"

--------------To change the root password in gitlab community-----------
docker exec -it gitlab-runner-gitlab-1 /bin/bash

gitlab-rails console

user = User.find_by(username: 'root')
user.password = 'YourNewPassword'
user.password_confirmation = 'YourNewPassword'
user.save!



----------To remove the volumes
Remove-Item -Recurse -Force .\gitlab\config
PS C:\GitLab-Runner> Remove-Item -Recurse -Force .\gitlab\logs
PS C:\GitLab-Runner> Remove-Item -Recurse -Force .\gitlab\data
PS C:\GitLab-Runner> Remove-Item -Recurse -Force .\gitlab\config



--------------Errors------------
Cannot open Web IDE
The URL you're using to access the Web IDE and the configured OAuth callback URL do not match. This issue often occurs when you're using a proxy.

Could not find a callback URL entry for http://localhost/-/ide/oauth_redirect.
Contact your administrator or try to open the Web IDE again with another domain.


Login as admin -> Cannot open Web IDE
https://docs.gitlab.com/ee/user/project/web_ide/#update-the-oauth-callback-url

To update the OAuth callback URL:

On the left sidebar, at the bottom, select Admin.
Select Applications.
For GitLab Web IDE, select Edit.
Enter the OAuth callback URL. You can enter multiple URLs separated by newlines.

http://localhost/-/ide/oauth_redirect


--------- setup runner----
go to the project CICD -> Runners -> new project runner and enter a name and description


.\gitlab-runner.exe register  --url http://localhost  --token 

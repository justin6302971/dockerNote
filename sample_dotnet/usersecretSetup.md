# dotnet cli note


## commands
``` bash
# setup  <UserSecretsId>79e22329-4aea-46eb-bc74-c258ac907884</UserSecretsId> in csproj
#setup user secret for development
dotnet user-secrets set "Settings:Secret" "Hidden Secret" --project <csproj path>
dotnet user-secrets list --project --project <csproj path>
dotnet user-secrets remove "Settings:Secret" --project --project <csproj path>
dotnet user-secrets clear

#secret.json location 
# for mac: ~/.microsoft/usersecrets/<user_secrets_id>/secrets.json
# for windows: %APPDATA%\Microsoft\UserSecrets\<user_secrets_id>\secrets.json
```


## references
1. [Set up HTTPS on local with .NET Core and Docker](https://thegreenerman.medium.com/set-up-https-on-local-with-net-core-and-docker-7a41f030fc76)
2. [Store Secrets on .NET Core with Azure during development](https://thegreenerman.medium.com/store-secrets-on-net-core-during-development-33eec9ddd0b)
3. [How to manage user secrets in ASP.NET Core](https://www.infoworld.com/article/3576292/how-to-work-with-user-secrets-in-asp-net-core.html)
4. [microsoft doc](https://docs.microsoft.com/zh-tw/aspnet/core/security/app-secrets?view=aspnetcore-6.0&tabs=linux)
5. [setup tutorial video](https://www.youtube.com/watch?v=lcaDDxJv260&list=WL&index=1&t=3s)
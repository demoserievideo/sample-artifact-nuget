# Sample GitHub Artifacts to Nuget 

![.Net Core Package](https://github.com/demoserievideo/sample-artifact-nuget/workflows/.Net%20Core%20Package/badge.svg)

This repo is a sample, publishing nuget packages on GitHub Artifacts.

# Important things:

In your CSPROJ, you need to add this keys in your `<PropertyGroup>`

```
    <PackageId>PackageName</PackageId>
    <Version>1.0.1</Version>
    <Authors>Package Author</Authors>
    <Company>Package Company</Company>
    <GeneratePackageOnBuild>true</GeneratePackageOnBuild>
    <RepositoryUrl>https://github.com/<Organization>/<RepositoryName></RepositoryUrl>
```

In Your Action:
In .Net Setup Step, you need to add the URL of GitHub Packages and GitHub Token, like this:
```
    - name: Setup .NET Core
      uses: actions/setup-dotnet@v1
      with:
        dotnet-version: 3.1.101
        source-url: https://nuget.pkg.github.com/<organization>/index.json
      env:
        NUGET_AUTH_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```
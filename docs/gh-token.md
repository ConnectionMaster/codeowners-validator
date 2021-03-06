[← back to docs](./README.md)

# GitHub personal access token

The [valid_owner.go](./../internal/check/valid_owner.go) check requires the GitHub personal access token for the following reasons:

1. Information about organization teams and their repositories is not publicly available.
2. If you set GitHub Enterprise base URL, an unauthorized error may occur. 
3. For unauthenticated requests, the rate limit allows for up to 60 requests per hour. Unauthenticated requests are associated with the originating IP address. In a big organization where you have a lot of calls between your infrastructure server and the GitHub site, it is easy to exceed that quota. 

Instructions for creating a token can be found [here](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/#creating-a-token). The minimal scope required for the token is **read-only**, but the definition of this scope differs between public and private repositories.

#### Public repositories 

For public repositories, select `public_repo` and `read:org`:

![token-public.png](./assets/token-public.png) 

#### Private repositories 

For private repositories, select `repo` and `read:org`:

![token-public.png](./assets/token-private.png) 

The Codeowners Validator source code is available on GitHub. You can always perform a security audit against its code base and build your own version from the source code if your organization is more strict about the software run in its infrastructure.

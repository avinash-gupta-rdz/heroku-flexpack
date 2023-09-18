## Overview

This buildpack is designed for customizing the deployment process on Heroku. With this buildpack, you can:

1. Install custom packages.
2. Use a custom `Procfile` and optionally `app.json` if present alongside.
3. Use a custom `robots.txt`.
4. Write credentials from the environment to a PEM file.

## Steps to Use

### 1. Add the buildpack to your Heroku app:

To add this buildpack to your Heroku app, use the `heroku buildpacks:add` command:

```bash
heroku buildpacks:add https://github.com/your-repo/custom-heroku-buildpack.git
```

Make sure to replace `https://github.com/your-repo/custom-heroku-buildpack.git` with the actual URL to your buildpack repository.

### 2. Configure Environment Variables:

This buildpack relies on several environment variables:

- `PROCFILE`: Specify a path relative to your project root to a custom `Procfile`.
- `ROBOTXT`: Specify a path relative to your project root to a custom `robots.txt`.
- `PRIVATE_KEY`: The content of the private key.
- `PRIVATE_KEY_PATH`: The path where the private key should be written.

Set these environment variables using the Heroku CLI:

```bash
heroku config:set PROCFILE=your_procfile_path
heroku config:set ROBOTXT=your_robots.txt_path
heroku config:set PRIVATE_KEY=your_private_key_content
heroku config:set PRIVATE_KEY_PATH=desired_private_key_path
```

### 3. Deploy Your App:

After setting the buildpack and configuring the environment variables, deploy your app:

```bash
git push heroku master
```

## Notes:

- Ensure that the URLs or paths you set in the environment variables are correct to prevent deployment failures.
- This buildpack assumes that if a custom `Procfile` is provided, the `app.json` would be present in the same directory.
- The custom `robots.txt` file will be copied to the `public/` directory.
- Always be cautious about handling sensitive information like private keys. Ensure you manage and store these safely.

## Support:

For issues related to this buildpack, please raise an issue in the GitHub repository or contact the maintainers.

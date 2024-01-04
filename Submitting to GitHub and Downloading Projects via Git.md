Using the simplest [nzshop.cn homepage project](https://github.com/tallblacks/nzshop.cn) as an example, let's demonstrate how to submit a Linux server-side project to GitHub using Git and how to download a project from GitHub.

#### Submitting NZShop.CN's Homepage to GitHub
1. Create a repository on GitHub. Ensure that in Settings -> General -> Default branch, it is set to `main`.

2. Set up an SSH key for your GitHub account:
	The `ssh-keygen` command generates a new RSA key pair and prompts you to enter a file path to save the private key. You can choose the default path or customize it.
	If you prefer the default path (recommended), just press Enter. If you want to customize the path, type the desired path to save the private key and press Enter.
	Next, the system may ask for a password to protect the private key. You can choose to set a password or press Enter to skip.
```shell
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```
	
3. `ssh-keygen` will generate a key pair and display the path to the public key. Add the content of the public key to GitHub's Deploy keys. You can view and copy the public key using the following command:
```shell
cat /root/.ssh/id_rsa.pub
```

4. Enter the website's directory:
```shell
cd /data/nzshop
git init
git add .
git commit -m "Initial commit"
```

5. Associate the project's Git with the GitHub repository:
```shell
git remote add origin git@github.com:tallblacks/nzshop.cn.git
git remote -v

git remote set-url origin ... // Update
git remote remove origin // Delete
```

7. Check the branch name. If it is `master`, change it to `main`:
```shell
git branch
git branch -m master main
```

8. Code upload failed because README.md was added on the website. Merge first and then upload:
```shell
git push -u origin main
git pull origin main
git push -u origin main
```


#### Restoring NZShop.CN's Homepage from GitHub ####
```shell
git clone https://github.com/tallblacks/nzshop.cn.git
```
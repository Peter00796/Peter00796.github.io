
## How to create a Git Repo? 

Firstly, navigate to your folder where you wish to create the repo in your terminal 

---
Now Type in these commands 
```Shell
git init
```
---
Now open your browser, log in to your github account, create a new repository

Copy your SSH key 

then go back to your terminal, type in:

```Shell
git remote add origin <your_repo_SSH_key>
```
---
After this step, your remote repo is linked to your local directory 

---
Now we need to do the first commit, type in the following commands 
```Shell 
git add .
git commit -m "initial commit"
git push -u origin main 
```
Until this step, go back to your github repo, refresh the page, make sure that your local repo is there! 



## Git Commitment WorkFlow 
And this is important. 

When we are contributing to our final project through using git, here are a few things that you need to be aware of. 

### Using Branch
I have already created a `develop`branch that reflects the state of `main` and will serve as the integration branch for ongoing development.

Each time anyone starts working on a *new feature or task* , you should create a feature branch from `develop`. For instance, if you are starting to work on the *score_page_UI_design* or *Mouse_Movement_Detection*, you should always do these three lines below


```bash
git checkout develop 
```
 //this switches your branch to develop branch
```bash
git pull origin develop
```
//this ensures that you pull most recent code from remote repo
```bash
git checkout -b feature/feature_name 
```
// this creates a new feature branch at which you code!

Replace `feature_name` with a name that describes the feature, like `feature/add-player-movement`.


Then, After making changes, stage and commit the work to the feature branch. 
```bash
git add .
git commit -m "Add player movement mechanics"
git push origin feature/feature_name
```
Replace `feature_name` with a name of your branch.

## IMPORTANT
### **Create A Pull Request**:
Right now, at this stage that you've already pushed your code to the branch that you're working on. If you feel that your code functions well and ready to merge, you should merge to the `develop` branch. 
You should go to GitHub and creates a pull request to merge the `feature/feature_name` branch into `develop`.
How to create a pull request, check below>>>

1. **Navigate to Your Repository on GitHub**: Open your web browser and go to the main page of your repository on GitHub.
	1. ![[Pasted image 20231115164723.png]]
2. **Go to the 'Pull Requests' Tab**: Click on the "Pull Requests" tab near the top of the repository's page.
	1. ![[Pasted image 20231115164810.png]]
3. **New Pull Request**: Click on the "New pull request" button to start the process of creating a new pull request.
4. **Choose the Base and Compare Branches**:
    - In the "base" dropdown, select the branch you want to merge into, which will usually be the `develop` branch.
    - In the "compare" dropdown, select your feature branch, e.g., `feature/feature_name`.
5. **Review Your Changes**: GitHub will show you the differences between the two branches. You can review the changes to make sure everything is as expected.
6. **Create Pull Request**: Click on "Create pull request".
7. **Add Details to Your Pull Request** (optional):
    - Give your pull request a title that summarizes the changes or the feature.
    - Write a detailed description of what the pull request does, linking any relevant issues or tasks. This is important for historical context and helps reviewers understand your changes.
8. **Create the Pull Request**: Once you have filled in all the details, click on "Create pull request" to officially open the pull request.

**Merge:** 
We together review the merge step and merge it to develop 

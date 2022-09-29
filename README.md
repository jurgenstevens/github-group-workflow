# GitHub Group Workflow
![GHGWF49-83-173](https://user-images.githubusercontent.com/48702365/193153588-0a3d8095-5dec-41f9-855d-b1690129a9cd.png)

# Team Workflow

To help illustrate collaborating on a project using Git/GitHub, consider the following two roles you can fulfill: **Git Commander (Manager)** and **Git Minion (Programmer)**.

**Minions** will contribute code and issue pull requests, while **Commanders** integrate the code by merging the pull requests into the repo, while also contributing code themselves.

Start by reviewing this article from GitHub on the GitHub Flow. It will guide you through the what and why of this whole process.

[GitHub flow - GitHub Docs](https://docs.github.com/en/get-started/quickstart/github-flow)

For today's exercise, you'll be starting from an already created project - the steps you will follow will be different when you are building a project from scratch. Both methods are listed below for your convenience.

## For Your Own Projects (decoupled app)

###  🚨 For Git Commander ONLY  🚨

1. Create your front end repo on Github and your React app with the following command if you haven't already done so:
    ```bash
    npx create-react-app [your project name]
    ```
    
2. After connecting your app to your Github front end repo, ensure you have a remote named `origin`**:**
    
    ```bash
    git remote -v
    ```
    
3. THEN, create your backend repo on Github and your Express backend with the following command if you haven't already done so:
    ```bash
    npm init -y
    npm i express dotenv mongoose
    ```
    
4. Ensure you have a remote named `origin` **** after connecting your backend to your Github back end repo:
    
    ```bash
    git remote -v
    ```
    

# For All Projects After Setup

## Forking

### Minion


1. Identify the repo (or repos) created by your commander on GitHub.
2. In the browser, navigate to that repo and Fork it to your own account. 
3. Next, clone down your forked repo and `cd` into the project directory. 
    
    ```bash
    git clone https://github.com/<your-gh-username>/<repo-you-forked>.git
    cd <repo-name>
    ```
    
4. Add an upstream link to the commander’s repo as well:
    
    ```bash
    git remote add upstream https://github.com/<commander's-github-username>/<repo-you-forked>.git
    ```
    
5. Install your npm packages:
    
    ```bash
    npm i
    ```
    
6. Ensure that you have two remotes named `origin` & `upstream`: 
    
    ```bash
    git remote -v
    ```
    

## Working on Feature Branches

![https://i.imgur.com/B5CZSuT.png](https://i.imgur.com/B5CZSuT.png)



## Commander and Minion

1. Frequently ensure that you have the most recently merged code on your local computer:
    - Checkout the `main` branch with:
        
        ```bash
        git checkout main
        ```
        
        <aside>
        🚨⚠️ Only pull when you are on `main` ⚠️🚨
        
        </aside>
        
    - Now you can pull!
        
        ```bash
        git pull upstream main
        ```
        
        <aside>
        🚨⚠️ **Commanders** will always use `origin` in place of `upstream`. ⚠️🚨
        
        </aside>
        
2. Create a **feature branch** with the below command. The branch name should correspond with the feature that branch will implement. 
    
    ```bash
    git checkout -b <feature_branch_name>
    ```
    
    <aside>
    🚨 ***YOU SHOULD NEVER WRITE CODE WHILE IN THE `main` BRANCH!***
    
    </aside>
    
    <aside>
    🚨 ***YOU SHOULD NEVER WRITE CODE WHILE IN THE `main` BRANCH!***
    
    </aside>
    
    <aside>
    🚨 ***YOU SHOULD NEVER WRITE CODE WHILE IN THE `main` BRANCH!***
    
    </aside>
    
    # 🚨 🚨 🚨 🚨 ***YOU SHOULD NEVER WRITE CODE WHILE IN THE `main` BRANCH!* 🚨 🚨 🚨 🚨**
    
3. Write some code (Where should you not be writing your code?)
4. **When you have completed a feature:**
    - Commit your code as usual but push to the feature branch name on your GitHub Origin
        
        ```bash
        git push origin <feature_branch_name>
        ```
        
    - An example of what steps 2-4 will look like in the terminal is shown below:
        
![GHGWF-Line146](https://user-images.githubusercontent.com/48702365/193153821-17cbac9e-29a9-4379-9ae3-033585bdfccc.png)

        
5. In the browser, open your fork of the repo. Click on the **Pull requests** tab. From here, you should be able to click on the **Compare and pull request** button.
    
    <aside>
    ‼️ FYI, multiple commits from the same branch to the same branch will be grouped within a single open pull request.
    
    </aside>
    
6. You’ll see an **Open a pull request** window. If you’d like, you can include a comment. At the bottom of the page, click the **Create pull request** button. 
7. Go back to step #1.

## Merging Pull Requests

### Command**er**

1. Navigate to your project repo on Github. 
2. Click on the Pull requests tab. You should see a list of open pull requests. Let’s click on the pull request that our minion just submitted.
3. Click on the **Files changed** and **Commits** tabs to review the incoming changes.
4. In the **Files changed** window, notice how newly added code blocks have been highlighted in green, while lines that were removed are highlighted in red. 
5. After reviewing the code, return to the **Conversation** tab. If there are no conflicts, and the incoming code is acceptable, click the **Merge** button. 
    
    <aside>
    ⚠️ If there are changes that need to be made, reach out to the minion and have them make those changes. After making the necessary changes, the minion should inform the commander that an update has been made, and the pull request is ready for another review.
    
    </aside>
    
6. If the request has merge conflicts, the commander may decide to test and merge the pull request locally/manually by clicking **command line instructions** and following the steps listed.
7. After a merge, ensure your team members pull the recent changes into their local repo ASAP.


![GHGWF49-83-173](https://user-images.githubusercontent.com/48702365/193153588-0a3d8095-5dec-41f9-855d-b1690129a9cd.png)


## Minimizing Merge Conflicts (Commander and Minion)

1. Try to divide up work so that no one makes changes to the same file between merges.
2. When notified that branches have been merged into `main` by the commander, **immediately** bring your local repo up to date so that you are working with the latest and greatest:
    1. We’re going to need to checkout the `main` branch to update it, however, *sometimes* Git will not allow us checkout a different branch if there are uncommitted changes in the current branch. The solution is to either `stash` or `commit` the changes first. Please read [**this StackOverflow**](https://stackoverflow.com/questions/22053757/checkout-another-branch-when-there-are-uncommitted-changes-on-the-current-branch) for how to resolve this scenario if Git does not allow the next step and to read about why this is allowed sometimes and other times it isn't.
    2. Checkout the main branch:
        
        ```bash
        git checkout main
        ```
        
    3. Pull from the GitHub Commander's main branch:
        
        ```bash
        git pull upstream main
        ```
        
        <aside>
        ⚠️ **Commanders** will always use `origin` in place of `upstream`.
        
        </aside>
        
    4. Checkout into your feature branch:
        
        ```bash
        git checkout <feature-branch-name>
        ```
        
    5. Bring the latest code into your feature branch so that you are always developing with the newest version of the code:
        
        ```bash
        git merge main
        ```
        
3. Making frequent and small commits and pull requests will help minimize merge conflicts.

## Fixing Merge Conflicts Locally (Commander and Minion)

<aside>
💡 When merging the newest code in the main branch into your feature branch, it’s possible to create merge conflicts too. So commanders aren’t the only ones who get to enjoy fixing merge conflicts!

</aside>

1. You should be in your feature branch when the conflicts occurred.
    
    After you've done this look for files with an exclamation mark as shown below: these are the files that have conflicts in them. Conflicts are also listed in the command line when you ran the `git merge main` command. You can also see files with conflicts if you run the `git status` command as shown below.
    
   ![line225](https://user-images.githubusercontent.com/48702365/193155192-dbd96a69-79ee-4796-932a-dbdf43f09dde.png)

    ![line226](https://user-images.githubusercontent.com/48702365/193155242-8882de7a-dbec-4092-be56-15b49d156e85.png)

    Go to these files and browse through them. You'll arrive at sections that are formatted similarly to this:
    
![line231](https://user-images.githubusercontent.com/48702365/193155446-240cf5ec-32ca-4fa9-a48d-208d964f7c07.png)

    Notice the options above line 106. Most useful to you will be: **Accept Current Change**, **Accept Incoming Change**, and **Accept Both Changes**.
    
    You're able to see the current change highlighted in green (also note the Current Change text on line 106) and the incoming change highlighted in blue (note the Incoming Change text on line 112).
    
    When deciding what code to keep remember to ***consult with your teammates!***
    
    Below you can see the outcome of accepting the incoming change:
    
![line241](https://user-images.githubusercontent.com/48702365/193155492-0f5b89f0-c249-4d32-94b6-c629dfa789a9.png)
    
2. After fixing the commits, add and commit:
    
    ```bash
    git add .
    git commit -m "Fix merge conflicts"
    ```
    
3. Continue developing as usual.

## Fixing Conflicts in a Pull Request or Merge (Commander)

![line254](https://user-images.githubusercontent.com/48702365/193156487-57e0b5f4-6d2c-4929-9ff8-90a9af2244fb.png)

If everyone is always following all of the above steps there should never be conflicts that are introduced in a pull request, but it is something that will happen and shouldn't be stressed about. The commander has 2 options here. 

1. They can either have the minion complete step 2 from the **Minimizing Merge Conflicts (Commander and Minion)** section above and then complete the **Fixing Merge Conflicts Locally (Commander and Minion)** section after that. They can then commit the cleaned up code without conflicts, push, and the conflicts should be resolved.
2. They can fix the problem themselves.

The easiest way for a commander to fix the problem themselves is to follow the 2 steps in the **command line instructions** view. 

![Screen Shot 2022-07-13 at 5.06.25 PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d8d3d8f9-9e2c-4bd5-9933-ca0174c1aff1/Screen_Shot_2022-07-13_at_5.06.25_PM.png)

Start by ensuring your main branch up to date with the origin with:

```bash
git pull origin main
```

Next, run the commands under Step 1 in your project directory. This command creates a new branch using the minion’s name and the name of the feature branch, and also brings in existing code from main for comparison's sake.

```bash
git checkout -b teradaian-react-redux main
git pull https://github.com/teradaian/all-the-things.git react-redux
```

<aside>
🚨 Do not reference the above commands for this step, they will be unique to every pull request.

</aside>

![Screenshot of the terminal after running the above commands](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/942d9933-95e1-489e-9c25-6668aaef8c5a/Screen_Shot_2022-07-13_at_5.20.42_PM.png)

Screenshot of the terminal after running the above commands

After you've done this look for files with an exclamation mark as shown below: these are the files that have conflicts in them. Conflicts are also listed in the command line when you ran the `git merge main` command. You can also see files with conflicts if you run the `git status` command as shown below.

![line289](https://user-images.githubusercontent.com/48702365/193158740-d19bd14e-b3b6-4c30-b55e-255798656656.png)

![line291](https://user-images.githubusercontent.com/48702365/193158757-aa034c2c-c663-4cfb-a677-8c0188c96229.png)

Go to these files and browse through them. You'll arrive at sections that are formatted similarly to this:

![line295](https://user-images.githubusercontent.com/48702365/193158796-1138196e-30c9-46fd-b0a6-9e613712b3bd.png)

Notice the options above line 106. Most useful to you will be: **Accept Current Change**, **Accept Incoming Change**, and **Accept Both Changes**.

You're able to see the current change highlighted in green (also note the Current Change text on line 106) and the incoming change highlighted in blue (note the Incoming Change text on line 112).

When deciding what code to keep remember to ***consult with your teammates!***

Below you can see the outcome of accepting the incoming change:

![line305](https://user-images.githubusercontent.com/48702365/193158850-5953ff40-5f32-447b-a196-586153c6d2c5.png)

After you've done this make a commit and use the commands in step 2:

```bash
git add .
git commit -m "resolve conflicts"
```

```bash
git checkout main
git merge --no-ff teradaian-react-redux
git push origin main
```

<aside>
🚨 Do not reference the above commands for this step, they will be unique to every pull request.

</aside>

![line325](https://user-images.githubusercontent.com/48702365/193158890-f25545e5-eb1c-4cde-bf3c-abc4cf53efd2.png)

<img width="618" alt="line327" src="https://user-images.githubusercontent.com/48702365/193158917-c873888e-13f9-4fc4-8d30-8f630482e4c9.png">

Screenshot of the terminal after running the above commands

After entering the above commands in your terminal, you should see a new tab open up in VS Code. All you need to do is exit out of it and the new code should be merged with main. 

## Checking the Logs

To visualize the history of commits made to the repo we use the `git log` command. There are several options, but this format works well:

```bash
git log --decorate --graph --oneline
```

Hit the `**Q**` key to exit this prompt

# Resources 📖

Articles and tutorials on branching and workflows in Git:

https://nvie.com/posts/a-successful-git-branching-model/
What's new after the migration
==============================

Hi SEMS Mailinglist,

as you might know already, over the past time I've migrated all projects from trac to GitHub. This brings up some implications, I want to summarize here as short as possible:

  * all source code, every ticket and each wiki entry is now on GitHub. So if you want to commit a patch, open an issue, or edit a wiki page, please do so on GitHub :)
  * The wiki pages were migrated to be GitHub pages for better portability. They are accessible under https://semsproject.github.io/
  * It was not possible to migrate ticket owner ship. So if you want to be notified about certain things watch the project (the eye icon, giving a star does not enable notifications) or subscribe to a certain issue (you can do this in the issue detail view)
  * If you're not listed as contributor for a certain project, please check if the E-Mail address is added to your GitHub profile (you can have multiple)
    - In case GitHub does not know an E-Mail address (i.e. nobody added it to their profile) the commits of this person are left out of the statistics 
  * Since we've done this step to preserve things for the cruel and cold world after SEMS, it would be nice if you help me adding/improving the documentation of the projects.
    - I appreciate every link, note, comment, etc!
  

Editing GitHub pages
--------------------

Editing GitHub pages aka. the former wiki pages involes now slightly more steps then before.
Either you can go to the project code page, switch the branch to "gh-pages", and edit the files via the WebUI, or you can clone the repository:

  * `git clone git@github.com:SemsProject/CombineArchive.git`
  * `git checkout gh-pages`

After you acquired access to the files either way, you can start editing them:

  * The pages are written in Markdown (`.md`)
    - A cheat sheet / reference card can be found here: https://guides.github.com/features/mastering-markdown/
  * In some repositories there are still `.wiki` files around. These files are just kept around so I can cross-check the Markdown manually, when the automatic conversion has done something quirky.
    - Please don't edit them, they don't affect the GitHub pages anyway.
  * Most of these repos also contain a link from `index.md` to `WikiStart.md`. This is also for legacy reasons, since GitHub does not recognize WikiStart as index page. Please simply edit WikiStart.md instead.
  * For links to other Markdown files within the same repository, simply use the filename as a link without extension. Links in Markdown are not auto-generated, you need to use the Markdown link syntax.
  * If you want to cross-link to a different project, please use absolute URLs. E.g. https://semsproject.github.io/CombineArchive/BuildCombineArchive
  * The overview page (https://semsproject.github.io/) is generated from a special project (https://github.com/SemsProject/SemsProject.github.io)

Once you've done editing, don't forgett to commit the changes and push them back to GitHub
  
  * `git commit -a`
  * `git push origin gh-pages`
  * it takes a couple of minutes until your changes will be visible to GitHub.io


Create GitHub pages for a new project
-------------------------------------

To create GitHub pages for a new project, you need to create an orphan branch:

  * cd into git repository
  * `git checkout --orphan gh-pages`
  * `rm -rf .` yes this deletes all files in the current repository, but fear not! Git saved them in the master branch.
  * create a `_config.yml` with
    ```yaml
    theme: jekyll-theme-minimal
    safe: False
    ```
  * write your Markdown (don't forget to create an `index.md`)
  * `git add .`
  * `git commit`
  * `git push origin gh-pages`
  * Your GitHub pages should now be available under `https://semsproject.github.io/<project_name>/`
  * ???
  * Profit!

**If I forgot to mention something, don't hesitate to drop me an E-Mail**

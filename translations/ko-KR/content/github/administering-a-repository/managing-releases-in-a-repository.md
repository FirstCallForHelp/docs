---
title: Managing releases in a repository
intro: You can create releases to bundle and deliver iterations of a project to users.
redirect_from:
  - /articles/creating-releases
  - /articles/listing-and-editing-releases/
  - /articles/editing-and-deleting-releases
  - /articles/managing-releases-in-a-repository
  - /github/administering-a-repository/creating-releases
  - /github/administering-a-repository/editing-and-deleting-releases
permissions: 'Repository collaborators and people with write access to a repository can create, edit, and delete a release.'
versions:
  free-pro-team: '*'
  enterprise-server: '*'
---

### About release management

You can also publish an action from a specific release in {{ site.data.variables.product.prodname_marketplace }}. For more information, see "[Publishing an action in the {{ site.data.variables.product.prodname_marketplace }}](/actions/creating-actions/publishing-actions-in-github-marketplace)."

{% if currentVersion == "free-pro-team@latest" or currentVersion ver_gt "enterprise-server@2.22" %}
You can choose whether {{ site.data.variables.large_files.product_name_long }} ({{ site.data.variables.large_files.product_name_short }}) objects are included in the ZIP files and tarballs that {{ site.data.variables.product.product_name }} creates for each release. For more information, see "[Managing {{ site.data.variables.large_files.product_name_short }} objects in archives of your repository](/github/administering-a-repository/managing-git-lfs-objects-in-archives-of-your-repository)."
{% endif %}

{% if currentVersion == "free-pro-team@latest" or currentVersion ver_gt "enterprise-server@2.19" %}
{% tip %}

**Tip**: You can also manage releases using the {{ site.data.variables.product.prodname_cli }}. For more information, see "[`gh release`](https://cli.github.com/manual/gh_release)" in the {{ site.data.variables.product.prodname_cli }} documentation.

{% endtip %}
{% endif %}

### Creating a release

{{ site.data.reusables.repositories.navigate-to-repo }}
{{ site.data.reusables.repositories.releases }}
3. Click **Draft a new release**. ![Releases draft button](/assets/images/help/releases/draft_release_button.png)
4. Type a version number for your release. Versions are based on [Git tags](https://git-scm.com/book/en/Git-Basics-Tagging). We recommend naming tags that fit within [semantic versioning](http://semver.org/). ![Releases tagged version](/assets/images/help/releases/releases-tag-version.png)
5. Use the drop-down menu to select the branch that contains the project you want to release. ![Releases tagged branch](/assets/images/help/releases/releases-tag-branch.png)
6. Type a title and description for your release. ![Releases description](/assets/images/help/releases/releases_description.png)
7. Optionally, to include binary files such as compiled programs in your release, drag and drop or manually select files in the binaries box. ![Providing a DMG with the Release](/assets/images/help/releases/releases_adding_binary.gif)
8. To notify users that the release is not ready for production and may be unstable, select **This is a pre-release**. ![Checkbox to mark a release as prerelease](/assets/images/help/releases/prerelease_checkbox.png)
9. If you're ready to publicize your release, click **Publish release**. To work on the release later, click **Save draft**. ![Publish release and Draft release buttons](/assets/images/help/releases/release_buttons.png)

You can also automatically create a release from the command line or in a script. For more information, see "[Releases](/v3/repos/releases/#create-a-release)."

### Editing a release

{{ site.data.reusables.repositories.navigate-to-repo }}
{{ site.data.reusables.repositories.releases }}
3. On the right side of the page, next to the release you want to edit, click **Edit release**. ![Edit a release](/assets/images/help/releases/edit-release.png)
4. Edit the details for the release in the form, then click **Update release**. ![Update a release](/assets/images/help/releases/update-release.png)

### Deleting a release

You must remove all binary files attached to a release before you can delete a release.

{{ site.data.reusables.repositories.navigate-to-repo }}
{{ site.data.reusables.repositories.releases }}
3. Click the name of the release you wish to delete. ![Link to view release](/assets/images/help/releases/release-name-link.png)
4. In the upper-right corner of the page, click **Delete**. ![Delete release button](/assets/images/help/releases/delete-release.png)
5. Click **Delete this release**. ![Confirm delete release](/assets/images/help/releases/confirm-delete-release.png)
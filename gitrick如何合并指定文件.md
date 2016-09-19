# Git trick 如何从一个分支中合并指定的文件 #
> http://jasonrudolph.com/blog/2009/02/25/git-tip-how-to-merge-specific-files-from-another-branch/

### git checkout ###

    git checkout source_branch <paths> ...

我们可以简单的通过git checkout source_branch（目标分支）<paths>（指定文件的路径） 

    $ git branch
    * master
      twitter_integration
    $ git checkout twitter_integration app/models/avatar.rb db/migrate/20090223104419_create_avatars.rb test/unit/models/avatar_test.rb test/functional/models/avatar_test.rb
    $ git status
    # On branch master
    # Changes to be committed:
    #   (use "git reset HEAD <file>..." to unstage)
    #
    #	new file:   app/models/avatar.rb
    #	new file:   db/migrate/20090223104419_create_avatars.rb
    #	new file:   test/functional/models/avatar_test.rb
    #	new file:   test/unit/models/avatar_test.rb
    #
    $ git commit -m "'Merge' avatar code from 'twitter_integration' branch"
    [master]: created 4d3e37b: "'Merge' avatar code from 'twitter_integration' branch"
    4 files changed, 72 insertions(+), 0 deletions(-)
    create mode 100644 app/models/avatar.rb
    create mode 100644 db/migrate/20090223104419_create_avatars.rb
    create mode 100644 test/functional/models/avatar_test.rb
    create mode 100644 test/unit/models/avatar_test.rb
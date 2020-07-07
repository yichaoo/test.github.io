```sh
docker run -it -p 9004:8000 --name demo-mkdown9004 --rm  -v ${PWD}:/docs squidfunk/mkdocs-material
```

```sh

  File "/usr/local/lib/python3.8/site-packages/mkdocs_git_revision_date_localized_plugin/plugin.py", line 36, in on_config
    self.util = Util(path=config["docs_dir"])
  File "/usr/local/lib/python3.8/site-packages/mkdocs_git_revision_date_localized_plugin/util.py", line 14, in __init__
    git_repo = Repo(path, search_parent_directories=True)
  File "/usr/local/lib/python3.8/site-packages/git/repo/base.py", line 181, in __init__
    raise InvalidGitRepositoryError(epath)
git.exc.InvalidGitRepositoryError: /docs/docs

```



```yaml
  - git-revision-date-localized:
      type: date
      allback_to_build_date: true
```

```yaml
plugins:
  - search: # necessary for search to work
      separator: '[\s\-\.]+'
  - awesome-pages
  # - git-revision-date-localized:
  #     type: date
  #     allback_to_build_date: true
```


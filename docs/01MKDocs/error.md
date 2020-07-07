```sh
docker run -it -p 9004:8000 --name demo-mkdown9004 --rm  -v ${PWD}:/docs squidfunk/mkdocs-material
```

```sh
INFO    -  Building documentation...
WARNING -  Config value: 'plugins'. Warning: ('allback_to_build_date', 'Unrecognised configuration name: allback_to_build_date')
WARNING -  Config value: 'dev_addr'. Warning: The use of the IP address '0.0.0.0' suggests a production environment or the use of a proxy to connect to the MkDocs server. However, the MkDocs' server is intended for local development purposes only. Please use a third party production-ready server instead.
Traceback (most recent call last):
  File "/usr/local/bin/mkdocs", line 8, in <module>
    sys.exit(cli())
  File "/usr/local/lib/python3.8/site-packages/click/core.py", line 829, in __call__
    return self.main(*args, **kwargs)
  File "/usr/local/lib/python3.8/site-packages/click/core.py", line 782, in main
    rv = self.invoke(ctx)
  File "/usr/local/lib/python3.8/site-packages/click/core.py", line 1259, in invoke
    return _process_result(sub_ctx.command.invoke(sub_ctx))
  File "/usr/local/lib/python3.8/site-packages/click/core.py", line 1066, in invoke
    return ctx.invoke(self.callback, **ctx.params)
  File "/usr/local/lib/python3.8/site-packages/click/core.py", line 610, in invoke
    return callback(*args, **kwargs)
  File "/usr/local/lib/python3.8/site-packages/mkdocs/__main__.py", line 133, in serve_command
    serve.serve(
  File "/usr/local/lib/python3.8/site-packages/mkdocs/commands/serve.py", line 141, in serve
    config = builder()
  File "/usr/local/lib/python3.8/site-packages/mkdocs/commands/serve.py", line 136, in builder
    build(config, live_server=live_server, dirty=dirty)
  File "/usr/local/lib/python3.8/site-packages/mkdocs/commands/build.py", line 236, in build
    config = config['plugins'].run_event('config', config)
  File "/usr/local/lib/python3.8/site-packages/mkdocs/plugins.py", line 94, in run_event
    result = method(item, **kwargs)
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


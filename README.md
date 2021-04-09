Github Issues to JIRA via JSON
==============================

JIRA now provides a JSON import facility that is vastly easier to use than the CSV one.

This is a simple script to generate a JSON file for this import from the GitHub Issues v3 API.

https://confluence.atlassian.com/pages/viewpage.action?pageId=293830712


Getting RUBY
------------
Easiest way is to just start a Docker ruby environment, then follow the instructions below.

```
docker run -v ~/dev/autoreduce:/autoreduce -it ruby:2.6 /bin/bash
```

Running
-------

Copy `config.yml.sample` to `config.yml` and edit the configuration to suit your needs.

Run the importer:
```bash
bundle install --path=vendor/bundle
bundle exec ruby g2j.rb
```

If you have a lot of issues (this tool makes at least 2 requests per issue), You can set a range of issue numbers to work around the GitHub API rate limit (< 5000 req/hour).

```bash
bundle exec ruby g2j.rb 1 1000
bundle exec ruby g2j.rb 1001 2000
etc.
```

TODO
----

- Attachments

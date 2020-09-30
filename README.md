# GitLab CI templates

We use these CI templates to reduce duplication and the maintenance burden for projects using GitLab's CI.

Just a friendly reminder: these are open-source and public, *so keep secrets out!*

## Usage

In your `.gitlab-ci.yml` file, add the following:

```yaml
include:
  - project: 'cap-public/ci/gitlab-ci-templates'
    file: '/elixir/pages.yml'

stages:
  - package
```

Make sure to include the stages from the includes - e.g. for [`elixir/mix.yml`](/elixir/mix.yml) you should add `test`
to `stages:`. In the example above, `package` was included as the `pages` job runs in that stage.

You can see example usage [here](https://gitlab.com/cap-public/packages/gitlab-header-auth/-/blob/master/.gitlab-ci.yml).

More information can be found [in the GitLab docs, here](https://docs.gitlab.com/ee/ci/yaml/includes.html). Note that 
the `remote: '[URL]'` syntax used in the official docs doesn't work with these templates - using the `project...file`
configuration (as shown in the usage example above) is recommended.

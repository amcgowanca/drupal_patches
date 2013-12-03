## Drupal Patches

A collection of patches that are commonly and regularly used during active development. This repository exists as a central holding area for all patch files that are applied to Drupal core, contributed modules and themes. More importantly, this repository is primarily used in conjunction with the [Drupal InstallKit](http://github.com/amcgowanca/drupal_installkit) and the [Drush](http://github.com/drush-ops/drush) make process.

### How to use these patches

As a result of various problems and challenges with managing patched codebases, these patches should not be applied directly to Drupal core, contributed modules and or themes. It is recommended that developers make use of these patches using the `drush make` process and a `drupal-org.make` file for applying patches to projects.

Each of the patch file links listed above are links to the RAW (plain text) version of the file. This is the URL that should be used within a `.make` file for specifying patches (`projects[project_name][patch][] = "http://..."`). This enables the ability to track and manage patched codebases with an ease of to revert patches.

### Contributing

If you are already using one of the patches listed above and feel that another one may be of use, you should fork this repository and *contribute* by submitting a new Pull Request containing your new additions.


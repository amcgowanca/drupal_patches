## Drupal Patches

A collection of patches that are commonly and regularly used during active development. This repository exists as a central holding area for all patch files that are applied to Drupal core, contributed modules and themes. More importantly, this repository is primarily used in conjunction with the [Drupal InstallKit](http://github.com/amcgowanca/drupal_installkit) and the [Drush](http://github.com/drush-ops/drush) make process.

### Patches: Drupal Core

#### Inheritable Profiles (developed by [@amcgowanca](http://github.com/amcgowanca))

##### Standard dependency check

This patch enables the ability to have inheritable (multiple) profiles allowing for one installation profile to depend on another. Drupal currently supports the inheritable themes or "base themes" but does not support this functionality for profiles. Therefore, this patch was created to be contributed back into the Drupal 7 core, in addition to it solving code management and product architecture problems previously faced.

***Patch File: [1356276-D7-inheritable-profiles-multi.patch](https://raw.github.com/imagex/imagex_patches/7.x/core/inheritable-profiles/1356276-D7-inheritable-profiles-multi.patch)***

##### Deep dependency check

This patch is derived from that of the inheritable profiles, however performs a deep dependency check for all modules, not just those listed within a profile's `.info` file.

***Patch File: [1356276-D7-inheritable-profiles-multi-enforce-dependencies.patch](https://raw.github.com/imagex/imagex_patches/7.x/core/inheritable-profiles/1356276-D7-inhertiable-profiles-multi-enforce-dependencies.patch)***

#### File Field - Issue: 2066275

Fixes the file field properties from being overwritten on load.

***Patch File: [2066275-file-field-load-merge-order.patch](https://raw.github.com/imagex/imagex_patches/7.x/core/2066275-file-field-load-merge-order.patch)***

#### Menu Translation - Issue: 951098, Comment: 50

This patch resolves the PHP Notice errors stating that `tab_root_map` is an undefined variable in the `_menu_translate` function located at `includes/menu.inc.`.

***Patch File: [undefined-menu-translate-notice-951098-50.patch](https://raw.github.com/imagex/imagex_patches/7.x/core/undefined-menu-translate-notice-951098-50.patch)***

### Patches: Contributed Modules

#### Features - Issue: 927566, Comment: 72

This patch enhances features method of identifying menu links, ensuring that each menu link is unique. This patch allows menu links with the same URL to be exported and re-created during the installation.

Applies to the 2.0-rc2 version of Features.

***Patch File: [features-multiple-link-path-927566-72.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/features/features-multiple-link-path-927566-72.patch)***

#### Features - Issue: 5430938, Comment: 81

This patch enhances features by providing a new alter hook `hook_features_export_render_alter` which allows the final features code to be altered by being saved to file.
Related issue: [https://drupal.org/comment/5430938](https://drupal.org/comment/5430938)

Applies to the 2.x version of Features.

***Patch File: [features-1317054-81.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/features/features-1317054-81.patch)***

#### Features Override - Issue: 1970474, Comment: 5

This patch solves a PHP notice error that identifies an array to string conversion that occurs when viewing the features/features_override page. The error also affects the visual representation of the exports.

***Patch File: [features_override-php_array_to_string_notice-1970474.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/features_override/features_override-php_array_to_string_notice-1970474.patch)***

#### Libraries API - Inheritable Profiles (developed by [@amcgowanca](http://github.com/amcgowanca))

This patch enables the Libraries API module to take into consideration multiple profiles when performing a libraries directory search. This is a *required* patch if using the Inheritable Profiles patch listed above when using the Libraries API.

***Patch File: [libraries-inheritable-profiles-fix.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/libraries/libraries-inheritable-profiles-fix.patch)***

#### Taxonomy Access Fix - Issue: 1637446 (developed by [@amcgowanca](http://github.com/amcgowanca))

This patch allows for the permissions created by the Taxonomy Access Fix module to identify the vocabularies using the machine name of the vocabulary and not the vocabulary id. This patch also provides an update path for existing permissions stored within the `{role_permission}` table.

***Patch File: [taxonomy_access_fix-changes-vocab-vid-to-machinename-usage-1637446.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/taxonomy_access_fix/taxonomy_access_fix-changes-vocab-vid-to-machinename-usage-1637446.patch)***

### How to use these patches

As a result of various problems and challenges with managing patched codebases, these patches should not be applied directly to Drupal core, contributed modules and or themes. It is recommended that developers make use of these patches using the `drush make` process and a `drupal-org.make` file for applying patches to projects.

Each of the patch file links listed above are links to the RAW (plain text) version of the file. This is the URL that should be used within a `.make` file for specifying patches (`projects[project_name][patch][] = "http://..."`). This enables the ability to track and manage patched codebases with an ease of to revert patches.

### Contributing

If you are already using one of the patches listed above and feel that another one may be of use, you should fork this repository and *contribute* by submitting a new Pull Request containing your new additions.


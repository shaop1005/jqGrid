# free fork of jqGrid
======

jqGrid is a popular jQuery Plugin for displaying and editing data in tabular form. It has some other more sophisticated features, like subgrids, TreeGrids, grouping and so on.

jqGrid was developed mostly by [Tony Tomov](https://github.com/tonytomov) in the past and it was available under MIT/GPL-licences till the version 4.7.0 published Dec 8, 2014 (see [here](https://github.com/tonytomov/jqGrid/tree/v4.7.0)). Short time after that the license agreement was changed (see <a href="https://github.com/tonytomov/jqGrid/commit/1b2cb55c93ee8b279f15a3faf5a2f82a98da3b4c">here</a>) and new 4.7.1 version was <a href="https://github.com/tonytomov/jqGrid/tree/v4.7.1">published</a>.

The code from the GitHib repository is the fork of jqGrid 4.7.0 - the latest version available under MIT/GPL-licences. It will be provided under MIT/GPL-licences.

Below you can find short description of new features and bug fixes implemented in free jqGrid 4.10.0 (compared with version 4.10.0). The version is developed by [Oleg Kiriljuk](https://github.com/OlegKi), alias [Oleg](http://stackoverflow.com/users/315935/oleg) on the stackoverflow and [OlegK](http://www.trirand.com/blog/?page_id=393) on trirand forum.

Read [Wiki](https://github.com/free-jqgrid/jqGrid/wiki) for more detailed information about the features of free-jqGrid.

Free jqGrid can be used *for free*. You can still donate by clicking on the following button [![PayPayl donate button](https://www.paypalobjects.com/webstatic/en_US/btn/btn_donate_pp_142x27.png)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=JGTCBLQM2BYHG "Donate once-off to free jqGrid project using Paypal") or by sending money via Paypal to oleg.kiriljuk@ok-soft-gmbh.com with the comment "free jqGrid".

One can install the package with respect of [bower](http://bower.io/search/?q=free-jqgrid) by using "bower install free-jqgrid", with respect of [npm](https://www.npmjs.com/package/free-jqgrid) by using "npm install free-jqgrid" or from [NuGet](https://www.nuget.org/packages/free-jqGrid) by using "Install-Package free-jqGrid".

The repository is included on [cdnjs](https://cdnjs.com/libraries/free-jqgrid). So one can include CSS by using
```html
<link rel="stylesheet" href="//cdnjs.cloudflare.com/ajax/libs/free-jqgrid/4.10.0/css/ui.jqgrid.css">
```
If you skip `http:` and `https:` prefix in the URL then the prefix of the current page will be used. In the same way you can access JavaScript files by
```html
<script src="//cdnjs.cloudflare.com/ajax/libs/free-jqgrid/4.10.0/js/jquery.jqgrid.min.js"></script>
```
or
```html
<script src="//cdnjs.cloudflare.com/ajax/libs/free-jqgrid/4.10.0/js/jquery.jqgrid.src.js"></script>
```
All language files are available in `js/i18n` sub-folder and plugins under `plugins` sub-folder. For example
```html
<script src="//cdnjs.cloudflare.com/ajax/libs/free-jqgrid/4.10.0/js/i18n/grid.locale-de.js"></script>
```

In the same way free jqGrid can be loaded from jsDelivr CDN too (see [here](http://www.jsdelivr.com/#!free-jqgrid)). 
```html
<link rel="stylesheet" href="//cdn.jsdelivr.net/free-jqgrid/4.10.0/css/ui.jqgrid.css">
<script src="//cdn.jsdelivr.net/free-jqgrid/4.10.0/js/i18n/grid.locale-de.js"></script>
<script src="//cdn.jsdelivr.net/free-jqgrid/4.10.0/js/jquery.jqgrid.min.js"></script>
```

It somebody want to test the *latest* version of free jqGrid one can load it directly from GitHib using [RawGit](http://rawgit.com/) service:
```html
<link rel="stylesheet" href="//rawgit.com/free-jqgrid/jqGrid/master/css/ui.jqgrid.css">
<script src="//rawgit.com/free-jqgrid/jqGrid/master/js/i18n/grid.locale-de.js"></script>
<script src="//rawgit.com/free-jqgrid/jqGrid/master/js/jquery.jqgrid.src.js"></script>
```

Remark: the above URLs will be available *after* publishing the release of the version of 4.10.0

### Main new features and improvements implemented in the version 4.10.0.

* New `abortAjaxRequest` method, which allows to abort pending Ajax request (before receiving the answer from the server)
* New option `threeStateSort:true` is implemented. It change the default behavior on click on the column header. Instead of toogleing between ascending and descending sorting, it will be changed between three states: ascending, descending and unsorted.
* New option `multiPageSelection:true` is implemented. It works in combination with `multiselect:true` option. It allows 1) select some rows during loading just by filling the rowids in `selarrrow` parameter 2) the parameter `selarrrow` can hold now selected rows from *multiple pages*. Selection of some rows on one page, changing of the page, selection some rows on another page, returting to the previous page hold all previously selected rows. Sorting don't clear the selection.
* New option `maxHeight` allows to set `max-height` CSS property on bdiv. The new option can be good combined with default `height: "auto"` option. For example the option `maxHeight: 400` have no influence in case of small number of rows, but it reduces the maximal height of body of the grid (bdiv) to `400px`, the grid get not so many place on the page and the user have to use horizontal scroll bar (created on demand).
* New options of `editRow` allows easy to implement starting of inline editing inside of `onSelectRow` or `ondblClickRow` and **setting the focus on the cell which the user clicked**.
* New callback `subGridOptions.hasSubgrid` is implemented. It allows to remove "+" icon of subgrid from some rows which definitively have no subgrids (have empty subgrids).
* Essential improvement of performance of frozen columns espesially in scenario where the grid have many hidden rows (like data grouping with `groupCollapse: true` option in `groupingView`). The parameters of the event `jqGridResetFrozenHeights` allows to elliminate unneeded work.
* Essential improvement of performance of `autoResizeColumn` method used in `autoResizeColumn` and `autoResizeAllColumns` methods and in case of usage of `autoresizeOnLoad: true` option.

### The below is the full list of changes in the version 4.10.0.

* Bug fix in usage of `sortable:true` (`sortableColumns` method)
* New `abortAjaxRequest` method, which allows to abort pending Ajax request (before receiving the answer from the server)
* Bug fix in processing of sorting by the date `"0000-00-00"`
* Bug fix to process of <kbd>Enter</kbd> on navigator buttons only. It can be important in case of usage custom elements in the navigator bar.
* Bug fix in processing of filters of Advainced Searching after Reset button is previously pressed.
* Fix of the height of column resizer
* New option `multiPageSelection:true` is implemented. It works in combination with `multiselect:true` option. It allows 1) select some rows during loading just by filling the rowids in `selarrrow` parameter 2) the parameter `selarrrow` can hold now selected rows from *multiple pages*. Selection of some rows on one page, changing of the page, selection some rows on another page, returting to the previous page hold all previously selected rows. Sorting don't clear the selection.
* Performance improvements of `$.jgrid.parseDate`
* New callback `subGridOptions.hasSubgrid` is implemented. It allows to remove "+" icon of subgrid from some rows which definitively have no subgrids (have empty subgrids).
* Bug fix in `GridToForm` method in parsing of data, which contains `&#160;` symbol
* Update of `grid.inlinedit.js` to allow overwrite `$.jgrid.info_dialog` method.
* New option `multiPageSelection:true` is implemented.
* Bug fixes in frozen columns in creating of hdiv and sdiv
* New option `quickEmpty:"quickest"` is implemented and is default
* Allow to use `focusField` as DOM element or Event as option of `editRow`. New option `defaultFocusField` implemented in `editRow`. The new options allow easy to implement starting of inline editing inside of `onSelectRow` or `ondblClickRow` and **setting the focus on the cell which the user clicked**.
* Add small magrin for sorting icons (between the sorting icon(s) and the text of column header)
* Bug fix in calculation of the width of column headers in `getAutoResizableWidth`
* Bug fix of the icon of TreeGrid leaf
* Improve performance of `autoResizeColumn` method
* update frozen columns to work better with filter toolbar and `jqPivot`
* Bug fix in the code of `editRow` to make `keys:true` option correctly work with frozen columns.
* Improve performance `setRowData` with frozen columns
* Bug fix to support `focusField` which point to frozen column
* Improvement of the performance of frozen columns
* Bug fix of the frozen footer (fsDiv)
* Add new `$.jgrid.hasAllClasses` method
* New option `maxHeight` allows to set `max-height` CSS property on bdiv. The new option can be good combined with default `height: "auto"` option. For example the option `maxHeight: 400` have no influence in case of small number of rows, but it reduces the maximal height of body of the grid (bdiv) to `400px`, the grid get not so many place on the page and the user have to use horizontal scroll bar (created on demand).
* Bug fixes in setting the width of bdiv (in case of vertical scrollbar appears)
* Bug fixes in `groupingRender` in processing of multi-level grouping with `groupCollapse:true` and `showSummaryOnHide:false`
* `groupingToggle` method is full rewritten to better support frozen columns and to improve the performance
* Bug fix in `setGroupHeaders` to set `<thable>` always before `<btable>` in the hdiv
* `setFrozenColumns` method is changed to improve essentially the performance.
* The parameters of `jqGridResetFrozenHeights` event is changed to improve performence in `setFrozenColumns`
* Bug fix in internal `savePositionOnHide` function used in all methods of form editing to save the position of the form on closing. The position of the forms is correctly saved and restored now.

[README492.md](https://github.com/free-jqgrid/jqGrid/blob/master/README492.md) contains the readme of free jqGrid 4.9.2.
[README491.md](https://github.com/free-jqgrid/jqGrid/blob/master/README491.md) contains the readme of free jqGrid 4.9.1.
[README49.md](https://github.com/free-jqgrid/jqGrid/blob/master/README49.md) contains the readme of free jqGrid 4.9.
[README48.md](https://github.com/free-jqgrid/jqGrid/blob/master/README48.md) contains the readme of free jqGrid 4.8.

Many thanks to all, who sent bug reports and suggestions to improve free jqGrid!

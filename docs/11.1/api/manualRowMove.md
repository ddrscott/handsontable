---
title: ManualRowMove
metaTitle: ManualRowMove - Plugin - Handsontable Documentation
permalink: /11.1/api/manual-row-move
canonicalUrl: /api/manual-row-move
hotPlugin: true
editLink: false
---

# ManualRowMove

[[toc]]

## Description

This plugin allows to change rows order. To make rows order persistent the [Options#persistentState](@/api/options.md#persistentstate)
plugin should be enabled.

API:
- `moveRow` - move single row to the new position.
- `moveRows` - move many rows (as an array of indexes) to the new position.
- `dragRow` - drag single row to the new position.
- `dragRows` - drag many rows (as an array of indexes) to the new position.

[Documentation](@/guides/rows/row-moving.md) explain differences between drag and move actions. Please keep in mind that if you want apply visual changes,
you have to call manually the `render` method on the instance of Handsontable.

The plugin creates additional components to make moving possibly using user interface:
- backlight - highlight of selected rows.
- guideline - line which shows where rows has been moved.


## Options

### manualRowMove
  
::: source-code-link https://github.com/handsontable/handsontable/blob/0472af66268f29ceb64d1f046b74a05149cffe8d/../handsontable/src/dataMap/metaManager/metaSchema.js#L2660

:::

_manualRowMove.manualRowMove : boolean | Array&lt;number&gt;_

The `manualRowMove` option configures the [`ManualRowMove`](@/api/manualRowMove.md) plugin.

You can set the `manualRowMove` option to one of the following:

| Setting  | Description                                                                                               |
| -------- | --------------------------------------------------------------------------------------------------------- |
| `true`   | Enable the [`ManualRowMove`](@/api/manualRowMove.md) plugin                                               |
| `false`  | Disable the [`ManualRowMove`](@/api/manualRowMove.md) plugin                                              |
| An array | - Enable the [`ManualRowMove`](@/api/manualRowMove.md) plugin<br>- Move individual rows at initialization |

Read more:
- [Row moving &#8594;](@/guides/rows/row-moving.md)

**Default**: <code>undefined</code>  
**Example**  
```js
// enable the `ManualRowMove` plugin
manualRowMove: true,

// enable the `ManualRowMove` plugin
// at initialization, move row 0 to 1
// at initialization, move row 1 to 4
// at initialization, move row 2 to 6
manualColumnMove: [1, 4, 6],
```

## Methods

### destroy
  
::: source-code-link https://github.com/handsontable/handsontable/blob/0472af66268f29ceb64d1f046b74a05149cffe8d/../handsontable/src/plugins/manualRowMove/manualRowMove.js#L728

:::

_manualRowMove.destroy()_

Destroys the plugin instance.



### disablePlugin
  
::: source-code-link https://github.com/handsontable/handsontable/blob/0472af66268f29ceb64d1f046b74a05149cffe8d/../handsontable/src/plugins/manualRowMove/manualRowMove.js#L145

:::

_manualRowMove.disablePlugin()_

Disables the plugin functionality for this Handsontable instance.



### dragRow
  
::: source-code-link https://github.com/handsontable/handsontable/blob/0472af66268f29ceb64d1f046b74a05149cffe8d/../handsontable/src/plugins/manualRowMove/manualRowMove.js#L212

:::

_manualRowMove.dragRow(row, dropIndex) ⇒ boolean_

Drag a single row to drop index position.

**Emits**: [`Hooks#event:beforeRowMove`](@/api/hooks.md#beforerowmove), [`Hooks#event:afterRowMove`](@/api/hooks.md#afterrowmove)  

| Param | Type | Description |
| --- | --- | --- |
| row | `number` | Visual row index to be dragged. |
| dropIndex | `number` | Visual row index, being a drop index for the moved rows. Points to where we are going to drop the moved elements. To check visualization of drop index please take a look at [documentation](@/guides/rows/row-moving.md#drag-and-move-actions-of-manualrowmove-plugin). |



### dragRows
  
::: source-code-link https://github.com/handsontable/handsontable/blob/0472af66268f29ceb64d1f046b74a05149cffe8d/../handsontable/src/plugins/manualRowMove/manualRowMove.js#L226

:::

_manualRowMove.dragRows(rows, dropIndex) ⇒ boolean_

Drag multiple rows to drop index position.

**Emits**: [`Hooks#event:beforeRowMove`](@/api/hooks.md#beforerowmove), [`Hooks#event:afterRowMove`](@/api/hooks.md#afterrowmove)  

| Param | Type | Description |
| --- | --- | --- |
| rows | `Array` | Array of visual row indexes to be dragged. |
| dropIndex | `number` | Visual row index, being a drop index for the moved rows. Points to where we are going to drop the moved elements. To check visualization of drop index please take a look at [documentation](@/guides/rows/row-moving.md#drag-and-move-actions-of-manualrowmove-plugin). |



### enablePlugin
  
::: source-code-link https://github.com/handsontable/handsontable/blob/0472af66268f29ceb64d1f046b74a05149cffe8d/../handsontable/src/plugins/manualRowMove/manualRowMove.js#L110

:::

_manualRowMove.enablePlugin()_

Enables the plugin functionality for this Handsontable instance.



### isEnabled
  
::: source-code-link https://github.com/handsontable/handsontable/blob/0472af66268f29ceb64d1f046b74a05149cffe8d/../handsontable/src/plugins/manualRowMove/manualRowMove.js#L103

:::

_manualRowMove.isEnabled() ⇒ boolean_

Checks if the plugin is enabled in the handsontable settings. This method is executed in [Hooks#beforeInit](@/api/hooks.md#beforeinit)
hook and if it returns `true` than the [ManualRowMove#enablePlugin](@/api/manualRowMove.md#enableplugin) method is called.



### isMovePossible
  
::: source-code-link https://github.com/handsontable/handsontable/blob/0472af66268f29ceb64d1f046b74a05149cffe8d/../handsontable/src/plugins/manualRowMove/manualRowMove.js#L243

:::

_manualRowMove.isMovePossible(movedRows, finalIndex) ⇒ boolean_

Indicates if it's possible to move rows to the desired position. Some of the actions aren't possible, i.e. You can’t move more than one element to the last position.


| Param | Type | Description |
| --- | --- | --- |
| movedRows | `Array` | Array of visual row indexes to be moved. |
| finalIndex | `number` | Visual row index, being a start index for the moved rows. Points to where the elements will be placed after the moving action. To check the visualization of the final index, please take a look at [documentation](@/guides/rows/row-moving.md#drag-and-move-actions-of-manualrowmove-plugin). |



### moveRow
  
::: source-code-link https://github.com/handsontable/handsontable/blob/0472af66268f29ceb64d1f046b74a05149cffe8d/../handsontable/src/plugins/manualRowMove/manualRowMove.js#L165

:::

_manualRowMove.moveRow(row, finalIndex) ⇒ boolean_

Moves a single row.

**Emits**: [`Hooks#event:beforeRowMove`](@/api/hooks.md#beforerowmove), [`Hooks#event:afterRowMove`](@/api/hooks.md#afterrowmove)  

| Param | Type | Description |
| --- | --- | --- |
| row | `number` | Visual row index to be moved. |
| finalIndex | `number` | Visual row index, being a start index for the moved rows. Points to where the elements will be placed after the moving action. To check the visualization of the final index, please take a look at [documentation](@/guides/rows/row-moving.md#drag-and-move-actions-of-manualrowmove-plugin). |



### moveRows
  
::: source-code-link https://github.com/handsontable/handsontable/blob/0472af66268f29ceb64d1f046b74a05149cffe8d/../handsontable/src/plugins/manualRowMove/manualRowMove.js#L179

:::

_manualRowMove.moveRows(rows, finalIndex) ⇒ boolean_

Moves a multiple rows.

**Emits**: [`Hooks#event:beforeRowMove`](@/api/hooks.md#beforerowmove), [`Hooks#event:afterRowMove`](@/api/hooks.md#afterrowmove)  

| Param | Type | Description |
| --- | --- | --- |
| rows | `Array` | Array of visual row indexes to be moved. |
| finalIndex | `number` | Visual row index, being a start index for the moved rows. Points to where the elements will be placed after the moving action. To check the visualization of the final index, please take a look at [documentation](@/guides/rows/row-moving.md#drag-and-move-actions-of-manualrowmove-plugin). |



### updatePlugin
  
::: source-code-link https://github.com/handsontable/handsontable/blob/0472af66268f29ceb64d1f046b74a05149cffe8d/../handsontable/src/plugins/manualRowMove/manualRowMove.js#L133

:::

_manualRowMove.updatePlugin()_

Updates the plugin state. This method is executed when [Core#updateSettings](@/api/core.md#updatesettings) is invoked.



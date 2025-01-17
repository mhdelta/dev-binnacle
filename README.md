# Miguel Ángel Henao Software Engineer Binnacle

## Entry 1: Issue with custom cell renderer component for ag grid

**Problem:**
To refactor a component with an ag grid, one of the cells has a custom renderer and executes two functions that live on the parent component.

**Solution:**
Solution to rewrite this fast enough was to bind the parent's functions to two new parameters as [cellRendererParams](https://www.ag-grid.com/javascript-data-grid/component-cell-renderer/), and then call them from the params object in the renderer component. 

If I had more time, I'd move the logic from the parents components to the renderer component for a cleaner version.   

**Code Snippet:**
```typescript
{
 ...
  cellRendererParams: {
    edit: this.edit.bind(this),
    delete: this.delete.bind(this)
  }
}
...
delete() {
  this.params.delete(this.data?.id);
}
```

// add entry #2 for the following issue: z index of the cdk-overlay-component
## Entry 2: Issue with z-index of the cdk-overlay-component

**Problem:**
The z-index of the cdk-overlay-component was over 1000000 causing third-party components to be hidden behind it.

**Solution:**
The solution was to override the z-index of the cdk-overlay-container using ng-deep in the component.css file

**Code Snippet:**
```css
::ng-deep .cdk-overlay-container {
  z-index: 1000 !important;
}
```

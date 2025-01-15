# Miguel Ángel Henao Software Engineer Binnacle

## Entry 1: Issue with custom cell renderer component for ag grid

**Problem:**
To refactor a component with an ag grid, one of the cells has a custom renderer and executes two functions that live on the parent component.

**Solution:**
Solution to rewrite this fast enough was to bind the parent's functions to two new parameters as cellRendererParams, and then call them from the params object in the renderer component. 

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

# Problem

There is this problem where we have a form with multiple steps, for instance step 1 personal details and step two delivery.
We can solve this by making one big Form but that leaves some inconsistencies for partial submits and ends up being very hacky.
We can write our own wrapper for multiple forms but this will eventually trip up somewhere along the chain.

# Actions

The initial plan was to provide a wrapper that would accept steps, these steps have their own validation, ... Let's look at the shape
of a step:

```js
{
  onSubmit? (triggers onNextStep)
  validate?
  mapPropsToValues?/initialValues?
  shouldSubmitWhenInvalid
  component
}
```

This wrapper provides its own context that tracks submits.

Potential issue, what if we are allowing for invalid submits? We need to track all errors too this will be a bit harder but should be solvable

The wrapper additionally tracks the step we're on and could output some kind these steps have been completed and stuff for the step
component itself.

Ideally this could just be a hook that preprocesses the steps array and wraps them with Form...

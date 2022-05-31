# Additional Changes

To reproduce the error, I've added a `docs` config to the `preview.js` and extended the `Button.stories.js` with a `component` configuration.

```
// .storybook/preview.js

export const parameters = {
  ...
  docs: {
    extractArgTypes: (tag) => {
      console.log("tag", tag);
    },
  },
};
```

// stories/Button.stories.js

```
export default {
  ...
  component: "my-button",
  ...
};
```

# How to reproduce

Running Storybook with version v6.4.22, the `extractArgTypes` function is called, any version of Storybook starting with v6.5.0 is not calling `extractArgTypes` anymore.

When checking out this repository, you're running on 6.4.22, please upgrade manually to 6.5.\* by changing the version in the package.json.

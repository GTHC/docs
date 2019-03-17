# General React Components on GTHC

### What is a Component?

Technically, all of the react you are writing will be composing components, but just like we mentioned in [containers.md](/containers.md) (read that first), there is a difference between two types of components, "Smart" Components (aka containers), and "Dumb" Components (or just components). The main difference in implementation between the two is whether or not it is connected to redux store or not. Again this is explained in the [containers.md](/containers.md).

So, when building a component, remember the point is to break down components to its most reasonably simple form, therefore, the component can be reusable and easier to understand. One good visual example is the one right below, where a container is holding multiple components, and they are all essentially each broken down to more simpler elements.

![](https://www.kirupa.com/react/images/react_components_composable_72.png)

### Coding Practices

This is a list of things to keep in mind when writing components (this list will be updated when necessary):

* Follow ES6 Practices

  * If you are not familiar with what ES6 practices are and how to follow them, take a look and read this [medium article](https://engineering.musefind.com/our-best-practices-for-writing-react-components-dec3eb5c3fc8), which follows identical conventions to GTHC (but ignore anything we don't use like decorators). The truly best resource though is other code written before you or your fellow developers who are familiar with the practices.

* Do **NOT** connect the redux store to components, only containers.
* Pass down all redux actions from containers all the way down to needed components.
* Any code that is not easily understood by reading it (especially helper functions), comment and explain in short detail.

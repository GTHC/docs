# React Containers on GTHC

### What is a React Container?
A `Container` is an informal term that is used for higher-level components on the virtual DOM. They are technically just the same as any other React component, but they are different in their use case. Containers are typically the main collection of all sub components in an application, but it can also be more than that. In our use case, in order for a component to be a container, the following must be true:

* Routable Component

   * These are the components that end up having a route connected to it. This will be elaborated more in the routes README. For example, `Dashboard.jsx` renders `/app/dashboard`.
* Redux-Connected Component ("Smart" Component)

   * Our components are categorized as Smart or Dumb depending on their connection status with the Redux store. An example of a Redux-Connected component will be shown below.
* Component that is a collection of multiple, reusable sub-components, and this component is not a sub-component to any other component (unless it is for routing or it is the Navigation Bar).

    * Unlike "dumb" components, containers will typically be collection of multiple components that can also be reuseable, in the sense that the sub-component can be re-rendered for other components/containers. It is important to note that it is not impossible, and it is likely that sub-components can still be a collection of multiple components, but not at the scale of it's container.

#### Redux-Connected Container

__Note:__ Connecting to the redux store should be exclusive to the redux container. If a sub-component ever needs data from the redux store, it __must__ be passed down as a prop from its container.

Here is an example of what redux connection looks like:

```
import React, { Component } from 'react';

// redux
import { connect } from 'react-redux';
import { bindActionCreators } from 'redux';

// redux actions
import {
  foo,
  bar,
} from './../actions/foobar';

class Container extends Component {
  ...
  render () {
    ...
  }
}

// connecting to redux

const mapStateToProps = (state) => {
  return {
    exampleState: state.exampleState,
  };
};

const mapDispatchToProps = (dispatch) => {
  return bindActionCreators(
    {
      foo,
      bar,
    },
    dispatch);
};

export default connect(mapStateToProps, mapDispatchToProps)(Container);

export {
  Container
};

```

Unlike a normal component, this react component goes through the process of connecting to the Redux store, thus, what is exported by default is the "Smart Component", rather what you typically see in a "Dumb Component":

```
import React, { Container } from 'react';

class Example extends Component {
  ...
}

export default Example;

```

A good diagram to refer to would be this, which visualizes the relationship between the Redux Store, the containers, and components:

![](https://i.imgur.com/UhuNXtw.jpg)

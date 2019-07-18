# JavaScript Best Practices
*A collection of JavaScript best practices*

> **Note**: this guide talks about best practices, instead of style guide.

## Table of Contents

  1. [The Bouncer Pattern](#the-bouncer-pattern)
  1. [Switch to Object Literal](switch-to-object-literal)

## The Bouncer Pattern

  - Use `multiple early exist/returns` rather than single exit/return.
    > Why? this increases readbility and is easy to understand

    ```javascript
    // bad
    function transformData(rawData) {
      let data;

      if(!rawData) {
        data = [];
      } else if(rawData.length === 1) {
        data = rawData;
      } else {
        data = rawData.map(item => item);
      }

      return data;
    }
    
    // good
    function transformData(rawData) {
      // check if no data
      if (!rawData) {
        return [];
      }

      // check for specific/edge case
      if (rawData.length == 1) {
        return [];
      }

      // actual function code goes here
      return rawData.map((item) => item);
    }
    ```

**[⬆ back to top](#table-of-contents)**


## Switch to Object Literal
  - Use object literal intead of switch statement

    > Why? This makes code more readable and understandable.

    ```javascript
    // bad
    let createType = null;
    switch (contentType) {
      case "post":
        createType = () => console.log("creating a post...");
        break;
      case "video":
        createType = () => console.log("creating a video...");
        break;
      default:
        createType = () => console.log('unrecognized content type');
    }

    createType();

    // good
    const contentTypes = {
      post: () => console.log("creating a post..."),
      video: () => console.log("creatinga  video..."),
      default: () => console.log('unrecognized content type')
    };

    const createType = contentTypes[contentType] || contentTypes['default'];
    createType();
    ```

**[⬆ back to top](#table-of-contents)**

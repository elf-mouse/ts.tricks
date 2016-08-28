## vendor.d.ts

```ts
declare module 'jquery' {
    let $: any;
    export = $;
}

// your.ts
import $ = require('jquery');
// or
// import * as $ from 'jquery';
```

```ts
declare module 'package-dependencies-name' {
    import * as React from 'react';

    interface IMyComponentProps {
        num?: number;
        str?: string;
        bool?: boolean;
        onClick?: {(event: any): void};
        // or
        onClick?(event: any) : void;
        // or
        onClick?: (event: any) => void;
    }

    class MyComponent extends React.Component<IMyComponentProps, {}> {

    }

    export default MyComponent;
    // or
    // export {MyComponent};
    // or
    // export = MyComponent;
}

// your.tsx
import MyComponent from 'package-dependencies-name';
// or
// import {MyComponent} from 'package-dependencies-name';
// or
// import MyComponent = require('package-dependencies-name');
```

---
layout: post
title:      "React/Redux Project"
date:       2020-09-26 09:28:00 -0400
permalink:  react_redux_project
---



Thee final project! We are here! You probably will see a lot of exclamation points in this blog due to my excitement and feeling proud of not only what I did, but what I have learned!

Speaking of what I learned, let's go ahead and start with `mapStateToProps`


Honestly, its more intimidating than it looks. The meaning is in the name. You are MAPPING the STATE to PROPS. For example:

```
const mapStateToProps = (state) => {
    return{ 
        companies: state.companies,
        search: ' '
    }
}
```

```companies: state.companies``` is providing the prop with information that has come from your redux.
```search: ' '``` allows you to update your local state that will activate a render based on the code you have added.

There goes the word that holds all the magic #Redux!

!(https://res.cloudinary.com/practicaldev/image/fetch/s--VtRaY29J--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://thepracticaldev.s3.amazonaws.com/i/fewc8ez6r2e2agah717y.png/)


[Code](https://github.com/emerykurt/tech-tribe)
[Video](https://youtu.be/6ZTHB4hdLxw)

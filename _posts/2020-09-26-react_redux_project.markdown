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
        search: ' '
				companies: state.companies,
    }
}
```

```search: ' '``` allows you to update your local state that will activate a render based on the code you have added.
```companies: state.companies``` is providing the prop with information that has come from your redux.

There goes the word that holds all the magic #Redux! Redux really is like the circle of info.

![](http:////imgur.com/DadA3PH)

Your #Action which would be your #Fetch from API, return a promise, convert the promise int a readable JSON, then it dispatch to you #Reducers. 

```
export const fetchCompanies = () => {
    return(dispatch) => {
        return fetch('http://localhost:3000/companies')
        .then(res => res.json())
        .then( (json) => {
            dispatch({type:"SET_COMPS", payload: json.data})
        })

    }
}
```

In the reducer (based upon the dispatch type it will change the state of your container.

```
export default (state = [], action) => {
    // debugger
    switch(action.type){
        case "SET_COMPS":
            return [...action.payload];
        case "ADD_COMPS":
                return [...state, action.payload];
        case "SEARCH":{
            // debugger
            const {value} = action
            const companies = state.filter((company) => company.attributes.name.includes(value))
            return {...companies}
        } 
        default:
            return state;
    }
}
```

Guess where it takes you??

![](http:////imgur.com/qPU8oXH)


`mapStateToProps`

![](http:////imgur.com/a/9gfoZ)


Check out my full frontend code at:
[Code](https://github.com/emerykurt/tech-tribe)

Watch a live demo of my app at:
[Video](https://youtu.be/6ZTHB4hdLxw)

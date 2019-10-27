# useContext

```javascript
import React, { createContext } from 'react'

// 0. AppContext 생성
const AppContext = createContext()

const App = () => {
  const user = {
    nickname: 'danuel',
    isAdmin: true
  }

  return (
    <AppContext.Provider value={user}>
      <div>
        <Posts />
      </div>
    </AppContext.Provider>
  )
}

// 1. PostsContext 생성
const PostsContext = createContext()

const Posts = () => {
  const posts = [
    {
      title: 'useContext 알아보기',
      content: '이번 편에서는 React Context를 ...'
    }
  ]

  return (
    <PostsContext.Provider value={posts}>
      <Children />
    </PostsContext.Provider>
  )
}

// 2. user와 posts를 가져와 화면에 보여주기
const Children = () => (
  <AppContext.Consumer>
    {user => (
      <PostsContext.Consumer>
        {posts => {
          let label = 'user'
          if (user.isAdmin) {
            label = 'admin'
          }

          return (
            <div>
              <div>{label}</div>
              <div>{user.nickname}</div>
              <div>{posts.map((post, index) => (
                <div key={index}>
                  <div>{post.title}</div>
                  <div>{post.content}</div>
                </div>
              ))}
            </div>
          )
        }}
      </PostsContext.Consumer>
    )}
  </AppContext.Consumer>
)
```

```javascript
import React, { createContext, useContext } from 'react'

// 0. AppContext 생성
const AppContext = createContext()

const App = () => {
  const user = {
    nickname: 'danuel',
    isAdmin: true
  }

  return (
    <AppContext.Provider value={user}>
      <div>
        <Posts />
      </div>
    </AppContext.Provider>
  )
}

// 1. PostsContext 생성
const PostsContext = createContext()

const Posts = () => {
  const posts = [
    {
      title: 'useContext 알아보기',
      content: '이번 편에서는 React Context를 ...'
    }
  ]

  return (
    <PostsContext.Provider value={posts}>
      <Children />
    </PostsContext.Provider>
  )
}

// 2. user와 posts를 가져와 화면에 보여주기
const Children = () => {
  const user = useContext(AppContext)
  const posts = useContext(PostsContext)

  let label = 'user'
  if (user.isAdmin) {
    label = 'admin'
  }

  return (
    <div>
      <div>{label}</div>
      <div>{user.nickname}</div>
      <div>{posts.map((post, index) => (
        <div key={index}>
          <div>{post.title}</div>
          <div>{post.content}</div>
        </div>
      ))}
    </div>
  )
}
```

> https://ko.reactjs.org/docs/hooks-reference.html#usecontext

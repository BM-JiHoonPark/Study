Next.js에서 데이터를 사용해 페이지를 정적 생성 시 두 가지의 Function을 사용할 수 있는데

외부 데이터를 가져오는 getStaticProps Function과

동적 라우팅 사용 시 사전 렌더링할 페이지 경로를 가져오는 getStaticPaths Function이 있다.


getStaticProps

```
function Blog({ posts }) {
  return (
    <ul>
        <li>{post.title}</li>
    </ul>
  )
}

export async function getStaticProps() {
  const res = await fetch('https://.../posts')
  const posts = await res.json()

  return {
    props: {
      posts,
    },
  }
}

export default Blog
```

getStaticPaths

```
function Post({ post }) {
  return (
    <ul>
        <li>{post.title}</li>
    </ul>
  )
}

export async function getStaticPaths() {
  const res = await fetch('https://.../posts')
  const posts = await res.json()

  const paths = posts.map((post) => ({
    params: { id: post.id },
  }))

  // API를 이용하지 않아도 가능하다.
  // const paths = [
  //     { params: { id: '1' } },
  //     { params: { id: '2' } },
  //     { params: { id: '3' } },
  //     { params: { id: '4' } }
  // ]

  return { paths, fallback: false }
}

export async function getStaticProps({ params }) {
  const res = await fetch(`https://.../posts/${params.id}`)
  const post = await res.json()

  return { props: { post } }
}

export default Post
```


참고자료 - Next.js 공식문서

```
https://nextjs.org/docs/basic-features/pages
```
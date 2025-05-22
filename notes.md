📝 Commit Notes: Initial Code Setup for Blogs App
✅ Steps Implemented:

1. Make API call using fetch
2. Set blogs data to state (To be implemented)
3. Show loader while fetching data (To be implemented)

```js
componentDidMount() {
  this.getBlogData()
}

getBlogData = async () => {
  const response = await fetch('https://apis.ccbp.in/blogs')
  const data = await response.json()
  console.log(data)
}

```
* Used componentDidMount() lifecycle method to make the API call.
* This ensures the API request is made after the component mounts, preventing render-blocking or undefined errors.
* Logs the fetched blog data in the console for now.

✅ This is the initial step. We'll later update the component to store this data in state and display a loader while fetching.


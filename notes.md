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

-------------- Commit2 Notes: Set Blogs Data to state--------------------------------------

# 📝 Commit Notes: Set Blogs Data to `state`

### 🧠 Explanation (in simple terms)

When we call the API, the data we get from the backend has object keys written in **snake_case**  
➡️ example: `image_url`, `avatar_url`

This is the common naming style used in **backend development**.

But in **frontend (React/JavaScript)**, we follow **camelCase**  
➡️ example: `imageUrl`, `avatarUrl`

So, before using that data in our app, we need to **convert those keys from snake_case to camelCase**.  
After converting, we can safely **update the component's state** with the cleaned data.


### ✅ Code Implementation

```js
const updateData = data.map(eachItem => ({
  id: eachItem.id,
  title: eachItem.title,
  topic: eachItem.topic,
  imageUrl: eachItem.image_url,
  avatarUrl: eachItem.avatar_url,
  author: eachItem.author,
}))
console.log(updateData)
this.setState({blogsData: updateData})
```
Used .map() to transform each object from the API.
Called this.setState() to store the updated blog data in the component’s state.

-----------
# 📝 Commit Notes: Show loader while fetching data 


✅ Installed and imported a loader component:

API calls take some time to get data from the server.  
So, it’s good practice to show a loading animation to the user while waiting.  

For this, I used a 3rd party React loader called `react-loader-spinner`.  
I imported the spinner like this:

```js
import { TailSpin } from 'react-loader-spinner'
```
✅ Then, I used conditional rendering to show either:

* The loader spinner while data is loading (isLoading is true)
* Or the blog items after data is fetched (isLoading is false)


```js
//Example code:
{isLoading ? (
  <TailSpin height={50} width={50} color="blue" ariaLabel="loading" />
) : (
  blogsData.map(item => <BlogItem blogData={item} key={item.id} />)
)}

```
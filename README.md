# Best practice when you write an API

## Some of the points to consider while writing an API:

  - Write for human.
  > Example: ```/users/{id}/card-number``` instead of ```/users/{id}/pin```.

  - Should use lower case letters.
  > Example: ```/users/{id}/pending-orders``` instead of ```/users/{id}/Pending_Orders```.

  - Separate words with dashes.
  > Example: ```/users/{id}/pending-orders``` instead of ```/users/{id}/pending_orders```.

  - Follow the naming pattern similar to the folder structure.

  - Use Hierarchy.

  - Keep in mind while designing an API is maintaining the version number in the API.
  
  - No trailing forward slash.
  > Example: ```/users/{id}/pending-orders``` instead of ```/users/{id}/pending-orders/``` and both should give the same output.

## Naming
  
  - Resource should be ```nouns``` not ```verbs```.
  > Example: /users/{id} instead of /get-user.

  - End-points methods should represent their work.
  > ```GET /posts``` Retrieves a list of posts.
  > ```GET /posts/1``` Retrieves a specific post.
  > ```POST /posts``` Create a new post.
  > ```PUT /posts/1``` Update all post #1 details.
  > ```PATCH /posts/1``` Partially update post #1.
  > ```DELETE /posts/1``` Delete post #1.

## Relationships

If there is a relationship between resources it can be represented like the following example:

Suppose that each posts has a comments so the end-points will be in the following form:

> ```GET /posts/1/comments``` Retrieves all comments that related to post number #1.

> ```GET /posts/1/comments/5``` Retrieves comment#5 related to post#1

> ```POST /posts/1/comments``` Create a new comment related in post#1

> ```PUT /posts/1/comments/5``` update comment #5 related in post#1

> ```PATCH /posts/1/comments/5``` Partially updates comment #5 related in post#1

> ```DELETE /posts/1/comments/5``` Delete comment #5 related in post#1

## Always use SSL

To secure your end-points. SSL helps to protect sensitive information such as logins, passwords, account details and cardholders information for e-commerce websites during Internet communication. All data over network will be encrypted.

## Always version your api

Because end-points may be needed to changes or updated so you need to design your end-points with a version that appeared in URL.

## Result filtering, sorting and searching

It’s best to keep the base resource URLs as lean as possible. Complex result filters, sorting requirements, and advanced searching

Use a unique query parameter for each field that implements filter, sorting or searching

### Filtering

if you want to get posts which only opened
> ```/posts?status=open``` so status is a query parameter that implements a filter.

### Sorting

like filtering a generic parameter sort can be used to describe sorting rules.

> ```GET /flights?sort=priority``` - Retrieves a list of flights in descending order of priority.

> ```GET /flights?sort=priority,created_at``` - Retrieves a list of flights in descending order of priority. Within a specific priority, older flights are ordered first.
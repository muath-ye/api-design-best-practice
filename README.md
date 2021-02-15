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

if you want to get flight which only opened
> ```/flight?status=open``` so status is a query parameter that implements a filter.

### Sorting

like filtering a generic parameter sort can be used to describe sorting rules.

> ```GET /flights?sort=priority``` - Retrieves a list of flights in descending order of priority.

> ```GET /flights?sort=priority,created_at``` - Retrieves a list of flights in descending order of priority. Within a specific priority, older flights are ordered first.

### Searching

Sometimes basic filters aren’t enough and you need the power of full text search.

This is a combining between filters and sorting.
> ```GET /flight?status=open&sort=priority``` Retrieves a list of opened flights in descending order of priority.

Example of search: 
> ```GET /flights?q=return&status=open&sort=priority,created_at``` - Retrieve the highest priority open flights mentioning the word ```return```

## Aliases for common queries

To make the API experience more pleasant for the average consumer, consider packaging up sets of conditions into easily accessible RESTful paths.

Example of alias:
> ```GET /flights/recently_opened```

## Prevent abuse

To prevent abuse you can limit API calls using:

> ```X-Rate-limit``` with status code response
```429 Too Many Requests```

> ```X-Rate-Limit-Limit``` - The number of allowed requests in the current period

> ```X-Rate-Limit-Remaining``` - The number of remaining requests in the current period

> ```X-Rate-Limit-Reset``` - The number of seconds left in the current period.

## Caching

HTTP provides a built-in caching framework! All you have to do is include some additional outbound response headers and do a little validation when you receive some inbound request headers.

There are 2 approaches: ETag and Last-Modified

## Errors

Just like an HTML error page shows a useful error message to a visitor, an API should provide a useful error message in a known consumable format.

API errors typically break down into 2 types: 400 series status codes for client issues & 500 series status codes for server issues.

JSON error body should provide a few things for the developer - a useful error message, a unique error code (that can be looked up for more details in the docs) and possibly a detailed description.

Example:
```json
{
  "code" : 1024,
  "message" : "Validation Failed",
  "errors" : [
    {
      "code" : 5432,
      "field" : "first_name",
      "message" : "First name cannot have fancy characters"
    },
    {
       "code" : 5622,
       "field" : "password",
       "message" : "Password cannot be blank"
    }
  ]
}
```

## HTTP Status code

HTTP response status codes indicate whether a specific HTTP request has been successfully completed.

Responses are grouped in five classes:

- Informational responses (100–199)
- Successful responses (200–299)
- Redirects (300–399)
- Client errors (400–499)
- Server errors (500–599)
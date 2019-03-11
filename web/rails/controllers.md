# Models on GTHC

[What is a controller and the MVC architecture?](https://en.wikipedia.org/wiki/Model–view–controller)

## When to create a controller?
Typically there won't be a need for a new controller, unless a new model has been created. Otherwise, using the controllers that already exist should be sufficient. 

## How to use a controller?
In our use case, controllers are necessary for handling all of our API routes, and what happens whenever certain HTTP requests hit a certain endpoint. This is all assigned in the `routes.rb` file which will direct any endpoint to a controller and function/method within the controller.

#### Custom Endpoint/Single Resource Routing

For example, if you want to understand how the hour breakdown data is collected from the API (it is the GET request on url, `api/v1/team/hours`), check `routes.rb` at line 52:

```
namespace :api do
  namespace :v1 do
    ...
    # team
    get 'team/hours', to: 'teams#team_hours'
    ...
  end
end
```

This is an example of how a `GET` request can be directed to a specific controller and function. The statement `get 'team/hours'` means grab any `GET` request at the url `<url>/team/hours`, and since the request is under the namespace of `api/v1`, the full url is `<url>/api/v1/team/hours`. The rest of the line, `to: 'teams#team_hours'`, is just the part that directs the request to a controller and function in the controller. `teams` is referring to the controller of the `Team` model, which would be found at `controllers/api/v1/teams_controller.rb` (make note of the namespace taking importance in the file location as well). `#team_hours` is just rails' way of identifying the function of where to run this `GET` request. So, if you go to the mentioned controller (at `./controllers/api/v1/team_controller.rb`), and find the function inside of the file named `team_hours`, you will find what exactly is running when an HTTP request of the method `GET` is called.


#### Resource Routing
While looking at `routes.rb`, you may have also noticed that some of the routes are declared using the `resources` function. For example,

```
namespace :api do
    namespace :v1 do
      resources :shifts, :teams, :captains, :users
      ...
    end
end
```

This is a function that rails provides that pre-generates signle resource routes for you. In the example above, the models `Shift`, `Team`, `Captain`, and `User` are all getting pre-generated routes, which make building APIs much easier as the pre-generated routes are the most common used endpoints needed for any model.

For more extensive detail on what and how to use a resource route on rails or anything related to routing and controllers on Rails, check their [official documentation here](https://guides.rubyonrails.org/routing.html#resource-routing-the-rails-default).

# Commands

### Create a project
```bash
$ rails new [project-name]
...
$ rails new blog
```
### Run Server
```bash
$ rails server
```
### Create a Controller
```bash
$ rails generate controller [ControllerName] [action]
...
$ rails generate controller Welcome index
```
* Most important of these are of course the controller, located
at app/controllers/welcome_controller.rb and the view, located
at app/views/welcome/index.html.erb.

* Folder Views for a controller: app/views/controller_name/

### Routing
```ruby
# config/routes.rb
Rails.application.routes.draw do
  get 'welcome/index'
 
  resources :articles # Collect of routes for making a CRUD
 
  root 'welcome#index' # Home Page
end
```
* You can check all app routes
```bash
$ rails routes
```
* Check this: [Routing Guide](http://guides.rubyonrails.org/routing.html)
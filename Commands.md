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

# Create CRUD's
### Generate Controllers
```bash
$ rails generate controller [ControllerName]
...
$ rails generate controller Articles
```
* Use Plural and CamelCase for names
### Forms on Rails
```erbruby
<%= form_with scope: :article, url: articles_path, local: true do |form| %>
  <p>
    <%= form.label :title %><br>
    <%= form.text_field :title %>
  </p>
 
  <p>
    <%= form.label :text %><br>
    <%= form.text_area :text %>
  </p>
 
  <p>
    <%= form.submit %>
  </p>
<% end %>
```
* scope: When you call form_with, you pass it an identifying scope for this form. In this case, it's the symbol :article. This tells the form_with helper what this form is for.
* url: Urls for the forms. To see urls options to use you can check `rails routes`
### Generate Models
```bash
$ rails generate model [ModelName] [attribute]:[data_type] [attribute]:[data_type]
...
$ rails generate model Article title:string text:text
```
* Use Singular and CamelCase for Model name
* Use Singular and lowercase for attributes

##### This generate a Model class and a Migrations, you can run migration using:
```bash
$ rails db:migrate
```
### Strong Parameters
* This a Security Rails feature for permitting send parameters from a form,
for access then we need to specify then:
```ruby
params.require(:form_scope_obj).permit(:param1, :param2)
# ...
params.require(:article).permit(:title, :text)
```
### redirect_to
* When you pass an Model object to this method, this redirect for Controller
show method
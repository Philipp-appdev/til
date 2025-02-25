Helper methods:
- Routes
  - Create flexible paths with: post "/movies" =>  "movies#create", as: :movies # movies_url and movies_path 
  - Resources :movies # creates all 7 CRUD routes
- Forms
  - <%= form_with(url: movies_path) do %>  <% end %>
    - OR: "<%= form_with(model: @movie, method: :patch) do |form| %>"
  - Labels: <%= label_tag :title_box, "Title" %>
    - OR:  <%= form.label :title %>
  - Input text field: 
    - <%= text_field_tag :query_title, @the_movie.title, {id: "title_box"} %>
      - Shorthand + nested:  <%= text_field_tag "movie[title]", @movie.title, id: "title_box" %>
      - OR:  <%= form.text_field :title %>
  - Input text box:  
    - <%= text_area_tag :query_description, @the_movie.description, {id: "description_box"} %>
    - Shorthand + nested: <%= text_area_tag "movie[description]", @movie.description, id: "description_box", rows: 3 %>
    - OR: <%= form.text_area :description, rows: 3 %>
  - Button
    - <%= button_tag "Create movie" %>
    - OR: <%= form.button %>
  - Patch: <%= form_with(url: movie_path(@the_movie), method: :patch) do %> <% end %>
- Controller
  - Shorthand: def show /  @the_movie = Movie.find(params.fetch(:id))  /  end
  - Shorthand for create with nested params: 
    - movie_attributes = params.require(:movie).permit(:title, :description)
    - @movie = Movie.new(movie_attributes)


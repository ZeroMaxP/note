### ruby new blog

先进去Gemfile换源

```tcl
source 'https://mirrors.tuna.tsinghua.edu.cn/rubygems'
```



### rails server

要在项目目录下,启动服务器



### rails generate scaffold post title:string text:text

创建title和text变量



### db:migrate

自动创建数据库表



### gedit app/views/posts/index.html.erb

修改index.html

```ruby
<h2>Hellow World!</h2>
<% @posts.each do |post| %>
<h3><%= link_to post.title,post %></h3>
<p>
<%= time_ago_in_words post.created_at %>
</p>
<p>
<%= truncate post.text %>
</p>
<% end %>
<p>
<%= link_to "写新博客", new_post_path %>
</p>
```



### vim app/views/posts/show.html.erb

修改博客页

```ruby
<h1><%= @post.title %><h1>
<%= @post.text %>
<p>
<%= link_to"返回" ,posts_path  %>
|
<%= link_to "编辑",edit_post_path(@post) %>
|
<%= link_to "删除",@post,:method =>:delete ,data:{confirm:"你要删除我吗"} %>
</p>
<h2>评论</h2>
<% @post.comments.each do |comment|%>
<p><%= comment.text %></p>
<p><%= time_ago_in_words comment.created_at%>ago.</p>
<p><%= link_to"删除评论",[@post,comment],:method =>:delete,data:{confirm:"删掉删掉"} %></p>
<%end%>


<%= form_for [@post,@post.comments.build] do |f| %>
	<p><%= f.text_area :text, :size=>'66x6'%></p>
	<p><%= f.submit"提交" %></p>
<%end%>
```



### rails g model comment post_id:integer text:text

### db:migrate

### vim config/routes.rb

```ruby
Rails.application.routes.draw do
  get 'comments/create'
  get 'comments/destroy'
  resources :posts do
	resources :comments
	end
  # For details on the DSL available within this file, see http://guides.rubyonrails.org/routing.html
end
```



### gedit app/models/post.rb

```ruby	
class Post < ApplicationRecord
	has_many :comments
end
```



### gedit app/models/comment.rb 

```ruby
class Comment < ApplicationRecord
	belongs_to:post	
end
```



### gedit app/controllers/comments_controller.rb

```ruby
class CommentsController < ApplicationController
  def create
  	@post = Post.find(params[:post_id])
	@comment = @post.comments.build(comment_params)
	@comment.save

	redirect_to @post
  end
	
  	def comment_params
	params.require(:comment).permit(:text)
	end

  def destroy
 	@comment= Comment.find(params[:id])
	@comment.destroy

	redirect_to @comment.post
  end
end
```



### 
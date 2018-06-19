### Rails CRUD

- ORM(Object Relational Mapper)

  - rails에서는 [ActiveRecord](http://guides.rubyonrails.org/active_record_basics.html)를 활용한다.

- Controller 생성

  ~~~console
  $rails g controller post index new create show deit update destroy
  ~~~

- Model 생성

  ~~~console
  $rails generate model post
  ~~~

  - `app/model/post.rb`
  - `db/migrate/20180619_create_posts.rb`

- `migration파일` 변경

  ```ruby
  class CreatePosts < ActiveRecord::Migration
    def change
      create_table :posts do |t|
        t.string :title
        t.text :body
        t.timestamps null: false
      end
    end
  end

  ```

  ~~~console
  $rake db:migrate
  == 20180619042745 CreatePosts: migrating ======================================
  -- create_table(:posts)
     -> 0.0054s
  == 20180619042745 CreatePosts: migrated (0.0057s) =============================


  ~~~

  - `db/schem.rb`에 반영이 되었는지 확인!

- CRUD

  - Create : `new`,`create`
  - Read : `show`
  - Update : `edit`,`update`
  - Destroy : `destroy`

- Create

  ~~~console
  irb(main) : 001:0 > Post.create(title: "제목",body: "내용")
  ~~~

- Read

  ~~~console
  irb(main) : 001:0 > Post.find(id)
  ~~~

- Update

  ~~~console
  irb(main) : 001:0 > Post.find(id)
  irb(main) : 002:0 > Post.update(title: "제목",body: "내용")
  ~~~

- Destroy

  ```console
  irb(main) : 001:0 > Post.find(id).destroy
  ```



### Rails flash message

```ruby
def destroy
   flash[:alert] = "삭제되었다"
end
```

~~~ruby
<%=flash[:alert] %>
~~~

### Rails partial

`app/views/layout/_flash.html.erb`

~~~erb
<%= render 'layout/flash' %>
~~~

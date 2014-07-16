cheatsheets
===========

Various bits of info and text.



    Field -> Data Type
    -----    ---------
    Id       int
    Phone #  varchar
    Email    varchar
    Desc     varchar
    Name     varchar
    Ssn      varchar
    Price    decimal, money, smallmoney
    ShipDate datetime
    Sex      bit
    Discont  bit
    Quantity int
    ZipCode  varchar
    
---------------------

    def quid(price)
        number_to_currency(price, :unit => "£")
    end
    
Then call it in views:

    quid(line_item.price)

--------------------------------------

    rails generate migration drop_tablename

& then update the below file:

db/migrate/timestamp_drop_tablename (updated in responce to Dan Wich's answer below)

        class DropTablename < ActiveRecord::Migration
          def up
            drop_table :tablename
          end
        
          def down
            create_table :tablename do |t|
              t.string :table_column
              t.references :anothertable
        
              t.timestamps        
            end
            add_index :tablenames, :anothertable_id
          end
        end
& then in the terminal:

    rake db:migrate
    rails destroy model model_name
    rake db:migrate
    git add .
    git commit -m "removed table/model_name"
    git push heroku master
    heroku run rake db:migrate
    heroku restart

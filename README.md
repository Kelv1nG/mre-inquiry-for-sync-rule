after docker compose build / up

*pg admin hosted at port :5050

couple of changes ive made compared to the demo
a) change lists.id and todos.id to autoincrementing pk
b) change todos.list_id as a foreign key to lists


-- Insert sample data into the 'lists' table
```shell
INSERT INTO lists (
    id, name, owner_id
)
VALUES
    (1, 'my_list1', 1),
    (2, 'my_list2', 1),
    (3, 'my_list3', 1);
```
-- Insert sample data into the 'todos' table
```shell
INSERT INTO todos (
    id, description, completed, list_id
)
VALUES
    (1, 'item1_list_1', true, 1),
    (2, 'item2_list_1', true, 1),
    (3, 'item1_list_2', true, 2),
    (4, 'item_2_list_2', true, 2),
    (5, 'item_1_list_3', true, 3),
    (6, 'item_2_list_3', true, 3);
```


initially for items for list_id=[1,2] are included
as declared in the sync rules
```shell
bucket_definitions:
  global:
    data:
      - SELECT * FROM lists

  todos:
    parameters:
      - SELECT id AS todo_id
        FROM todos
        WHERE list_id IN request.jwt() ->> 'list_id'
    data:
      - SELECT * FROM todos WHERE id = bucket.todo_id
```

jwt parmeters:
```shell
 {
  "sub": "1",
  "iat": 1734021891.3898826,
  "iss": "https://d9ae-2601-282-1800-d970-7da1-854e-b9a7-98d.ngrok-free.app",
  "aud": "powersync-dev",
  "exp": 1734022191,
  "list_id": [
    1,
    2
  ]
}
```

![image](https://github.com/user-attachments/assets/048724eb-6908-4916-8118-65e865978704)


after updating

-- Update the 'list_id' for a todo item
```shell
UPDATE todos
SET list_id = 2
WHERE id = 1;
```
todo id = 1 gets removed
![image](https://github.com/user-attachments/assets/e79e0678-1499-46b5-8cb5-de774ccd82f2)


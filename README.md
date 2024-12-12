after docker compose build / up

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

![image](https://github.com/user-attachments/assets/048724eb-6908-4916-8118-65e865978704)


after updating

-- Update the 'list_id' for a todo item
```shell
UPDATE todos
SET list_id = 2
WHERE id = 1;
```
item gets removed
![image](https://github.com/user-attachments/assets/e79e0678-1499-46b5-8cb5-de774ccd82f2)


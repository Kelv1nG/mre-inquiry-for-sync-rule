after docker compose build / up

-- Insert sample data into the 'lists' table
INSERT INTO lists (
    id, name, owner_id
)
VALUES
    (1, 'my_list1', 1),
    (2, 'my_list2', 1),
    (3, 'my_list3', 1);

-- Insert sample data into the 'todos' table
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


-- Update the 'list_id' for a todo item
UPDATE todos
SET list_id = 2
WHERE id = 1;

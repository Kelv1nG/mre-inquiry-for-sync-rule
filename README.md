after docker compose build / up

run in postgres

INSERT INTO lists(
 id, name, owner_id
)
VALUES
(1, 'my_list1', 1),
(2, 'my_list2', 1),
(3, 'my_list3', 1);

INSERT INTO todos(
 id, description, completed, list_id
)
VALUES
(1, 'item1_list_1', true, 1),
(2, 'item2_list_1', true, 1),
(3, 'item1_list_2', true, 2),
(4, 'item_2_list_2', true, 2),
(5, 'item_1_list_3', true, 3),
(6, 'item_2_list_3', true, 3);


try to change a todo to a different list_id

UPDATE todos
SET list_id = 2
WHERE "id" = 1

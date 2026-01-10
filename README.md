# SQL Theory

A collection of structured SQL theories and explanations that serves as a personal repository for learning and reference materials.

---

## 🌐 Language / Язык
[**English**](#sql-theory-english) | [**Русский**](#sql-theory-russian)

---

<a name="sql-theory-english"></a>
# SQL Theory (English)

The final part of the SQL SELECT query is illustrated in Figure 8.

Figure 1 illustrates numerical operators used in SQL clauses.

<p align="center">
  <img src="https://github.com/user-attachments/assets/71db239a-35bc-495b-a3fc-aeb811237f22" width="850" alt="Figure 1" />
  <br>
  <em><b>Figure 1. SQL numerical operators</b></em>
</p>

Figure 2 illustrates text operators used in SQL WHERE clauses.

<p align="center">
  <img src="https://github.com/user-attachments/assets/7655b7ec-f84a-4154-bd99-82e42a9fa39e" width="850" alt="Figure 2" />
  <br>
  <em><b>Figure 2. SQL text operators</b></em>
</p>

> [!NOTE]
> DISTINCT – Removing duplicate rows.

Figure 3 illustrates limiting results to a subset.

<p align="center">
  <img src="https://github.com/user-attachments/assets/30c9f76a-fef6-40a9-bb16-8c049448f185" width="400" alt="Figure 3" />
  <br>
  <em><b>Figure 3. Limiting results to a subset</b></em>
</p>

> [!NOTE]
> Positive latitude values correspond to the northern hemisphere, and positive longitude values correspond to the eastern hemisphere.

Figure 4 illustrates the use of an INNER JOIN to combine data from multiple tables.

<p align="center">
  <img src="https://github.com/user-attachments/assets/8d96ab87-4f75-4953-a4a4-f8a000af63db" width="500" alt="Figure 4" />
  <br>
  <em><b>Figure 4. INNER JOIN in SQL</b></em>
</p>

Figure 5 illustrates the use of LEFT, RIGHT, and FULL JOINs in SQL queries.

<p align="center">
  <img src="https://github.com/user-attachments/assets/fc8b80ba-128b-4254-99b3-5e0ef4a6e9a8" width="500" alt="Figure 5" />
  <br>
  <em><b>Figure 5. LEFT, RIGHT, and FULL JOINs in SQL</b></em>
</p>

Figure 6 illustrates common aggregate functions in SQL.

<p align="center">
  <img src="https://github.com/user-attachments/assets/10845c28-ddbf-4554-ae73-b5f5d8194228" width="850" alt="Figure 6" />
  <br>
  <em><b>Figure 6. SQL aggregate functions</b></em>
</p>

Figure 7 illustrates the use of the HAVING clause to filter grouped results in SQL queries.

<p align="center">
  <img src="https://github.com/user-attachments/assets/ec491f75-c811-4124-b22c-4a55f22a77e0" width="850" alt="Figure 7" />
  <br>
  <em><b>Figure 7. HAVING clause in SQL</b></em>
</p>

Figure 8 illustrates the structure and execution order of a complete SQL SELECT query.

<p align="center">
  <img src="https://github.com/user-attachments/assets/2b90c680-8c34-4ab5-bdfa-192cedd01bdf" width="600" alt="Figure 8" />
  <br>
  <em><b>Figure 8. Complete SQL SELECT query</b></em>
</p>

---

### Query order of execution

1. **FROM and JOINs** The FROM clause, and subsequent JOINs are first executed to determine the total working set of data that is being queried. This includes subqueries in this clause, and can cause temporary tables to be created under the hood containing all the columns and rows of the tables being joined.

2. **WHERE** Once we have the total working set of data, the first-pass WHERE constraints are applied to the individual rows, and rows that do not satisfy the constraint are discarded. Each of the constraints can only access columns directly from the tables requested in the FROM clause. Aliases in the SELECT part of the query are not accessible in most databases since they may include expressions dependent on parts of the query that have not yet executed.

3. **GROUP BY** The remaining rows after the WHERE constraints are applied are then grouped based on common values in the column specified in the GROUP BY clause. As a result of the grouping, there will only be as many rows as there are unique values in that column. Implicitly, this means that you should only need to use this when you have aggregate functions in your query.

4. **HAVING** If the query has a GROUP BY clause, then the constraints in the HAVING clause are then applied to the grouped rows, discard the grouped rows that don't satisfy the constraint. Like the WHERE clause, aliases are also not accessible from this step in most databases.

5. **SELECT** Any expressions in the SELECT part of the query are finally computed.

6. **DISTINCT** Of the remaining rows, rows with duplicate values in the column marked as DISTINCT will be discarded.

7. **ORDER BY** If an order is specified by the ORDER BY clause, the rows are then sorted by the specified data in either ascending or descending order. Since all the expressions in the SELECT part of the query have been computed, you can reference aliases in this clause.

8. **LIMIT / OFFSET** Finally, the rows that fall outside the range specified by the LIMIT and OFFSET are discarded, leaving the final set of rows to be returned from the query.

<p align="center">
  <img width="400" alt="sqlENG" src="https://github.com/user-attachments/assets/d1bc715e-2c69-4533-9ad9-fd99a1d6031e" />
</p>

---

Figure 9 illustrates the use of the INSERT statement to add data into a database table.

<p align="center">
  <img src="https://github.com/user-attachments/assets/f3fd3624-6786-4c16-b172-67198b550e8a" width="500" alt="Figure 9" />
  <br>
  <em><b>Figure 9. SQL INSERT statement</b></em>
</p>

Figure 10 illustrates the use of the UPDATE statement to modify existing data in a database table.

<p align="center">
  <img src="https://github.com/user-attachments/assets/57266ea8-b4ba-4e8d-8307-48da5bdfe8dd" width="500" alt="Figure 10" />
  <br>
  <em><b>Figure 10. SQL UPDATE statement</b></em>
</p>

Figure 11 illustrates the use of the DELETE statement to remove data from a database table.

<p align="center">
  <img src="https://github.com/user-attachments/assets/0c364a9d-0a70-4f9c-8b07-8bdd154bac8d" width="300" alt="Figure 11" />
  <br>
  <em><b>Figure 11. SQL DELETE statement</b></em>
</p>

Figure 12 illustrates the use of the CREATE TABLE statement to define a new database table schema.

<p align="center">
  <img src="https://github.com/user-attachments/assets/a78e84cf-78df-49ac-9d51-b9d242f913a5" width="600" alt="Figure 12" />
  <br>
  <em><b>Figure 12. SQL CREATE TABLE statement</b></em>
</p>

Figure 13 illustrates the use of the ALTER TABLE statement to add new columns to a database table.

<p align="center">
  <img src="https://github.com/user-attachments/assets/900d1960-bd06-493f-ad60-b54e3cae4dd7" width="500" alt="Figure 13" />
  <br>
  <em><b>Figure 13. SQL ALTER TABLE ADD COLUMN statement</b></em>
</p>

Figure 14 illustrates the use of the ALTER TABLE statement to remove columns from a database table.

<p align="center">
  <img src="https://github.com/user-attachments/assets/1db93cd9-a9e2-45a0-9830-8a3410237e4d" width="300" alt="Figure 14" />
  <br>
  <em><b>Figure 14. SQL ALTER TABLE DROP COLUMN statement</b></em>
</p>

Figure 15 illustrates the use of the ALTER TABLE statement to rename a database table.

<p align="center">
  <img src="https://github.com/user-attachments/assets/dd6cb1c6-57fb-437a-a3f8-5a10dd0b7c74" width="300" alt="Figure 15" />
  <br>
  <em><b>Figure 15. SQL ALTER TABLE RENAME TO statement</b></em>
</p>

Figure 16 illustrates the use of the DROP TABLE statement to remove a database table and its schema.

<p align="center">
  <img src="https://github.com/user-attachments/assets/8ef0c5b9-e34c-499a-ab1e-2fdb6f00f896" width="300" alt="Figure 16" />
  <br>
  <em><b>Figure 16. SQL DROP TABLE statement</b></em>
</p>

---

<a name="sql-theory-russian"></a>
# Теория SQL (Русский)

Заключительная часть SQL-запроса SELECT проиллюстрирована на рисунке 8.

Рисунок 1 иллюстрирует числовые операторы, используемые в SQL-выражениях.

<p align="center">
  <img src="https://github.com/user-attachments/assets/71db239a-35bc-495b-a3fc-aeb811237f22" width="850" alt="Figure 1" />
  <br>
  <em><b>Рисунок 1. Числовые операторы SQL</b></em>
</p>

Рисунок 2 иллюстрирует текстовые операторы, используемые в SQL-выражениях WHERE.

<p align="center">
  <img src="https://github.com/user-attachments/assets/7655b7ec-f84a-4154-bd99-82e42a9fa39e" width="850" alt="Figure 2" />
  <br>
  <em><b>Рисунок 2. Текстовые операторы SQL</b></em>
</p>

> [!NOTE]  
> DISTINCT — удаление дублирующихся строк.

Рисунок 3 иллюстрирует ограничение результатов до подмножества.

<p align="center">
  <img src="https://github.com/user-attachments/assets/30c9f76a-fef6-40a9-bb16-8c049448f185" width="400" alt="Figure 3" />
  <br>
  <em><b>Рисунок 3. Ограничение результатов до подмножества</b></em>
</p>

> [!NOTE]  
> Положительные значения широты соответствуют северному полушарию, а положительные значения долготы — восточному полушарию.

Рисунок 4 иллюстрирует использование INNER JOIN для объединения данных из нескольких таблиц.

<p align="center">
  <img src="https://github.com/user-attachments/assets/8d96ab87-4f75-4953-a4a4-f8a000af63db" width="500" alt="Figure 4" />
  <br>
  <em><b>Рисунок 4. INNER JOIN в SQL</b></em>
</p>

Рисунок 5 иллюстрирует использование LEFT, RIGHT и FULL JOIN в SQL-запросах.

<p align="center">
  <img src="https://github.com/user-attachments/assets/fc8b80ba-128b-4254-99b3-5e0ef4a6e9a8" width="500" alt="Figure 5" />
  <br>
  <em><b>Рисунок 5. LEFT, RIGHT и FULL JOIN в SQL</b></em>
</p>

Рисунок 6 иллюстрирует распространённые агрегатные функции в SQL.

<p align="center">
  <img src="https://github.com/user-attachments/assets/10845c28-ddbf-4554-ae73-b5f5d8194228" width="850" alt="Figure 6" />
  <br>
  <em><b>Рисунок 6. Агрегатные функции SQL</b></em>
</p>

Рисунок 7 иллюстрирует использование предложения HAVING для фильтрации сгруппированных результатов в SQL-запросах.

<p align="center">
  <img src="https://github.com/user-attachments/assets/ec491f75-c811-4124-b22c-4a55f22a77e0" width="850" alt="Figure 7" />
  <br>
  <em><b>Рисунок 7. Предложение HAVING в SQL</b></em>
</p>

Рисунок 8 иллюстрирует структуру и порядок выполнения полного SQL-запроса SELECT.

<p align="center">
  <img src="https://github.com/user-attachments/assets/2b90c680-8c34-4ab5-bdfa-192cedd01bdf" width="600" alt="Figure 8" />
  <br>
  <em><b>Рисунок 8. Полный SQL-запрос SELECT</b></em>
</p>

---

### Порядок выполнения запроса

1. **FROM и JOIN** Сначала выполняется предложение FROM и все последующие JOIN. На этом этапе формируется полный рабочий набор данных, который будет участвовать в запросе. Это включает подзапросы в данном разделе и может приводить к созданию временных таблиц, содержащих все столбцы и строки объединяемых таблиц.

2. **WHERE** После формирования рабочего набора данных применяются условия WHERE, которые фильтруют отдельные строки. Строки, не удовлетворяющие условиям, отбрасываются. Условия на этом этапе могут обращаться только к столбцам таблиц, указанных в FROM. Псевдонимы из SELECT обычно недоступны, так как вычисления в SELECT ещё не выполнены.

3. **GROUP BY** Оставшиеся после WHERE строки группируются по значениям столбцов, указанных в GROUP BY. В результате количество строк соответствует числу уникальных значений в этих столбцах. Как правило, GROUP BY используется вместе с агрегатными функциями.

4. **HAVING** Если в запросе используется GROUP BY, условия из HAVING применяются к уже сформированным группам. Группы, не удовлетворяющие условиям, отбрасываются. Аналогично WHERE, псевдонимы на этом этапе в большинстве СУБД недоступны.

5. **SELECT** Вычисляются все выражения, указанные в SELECT.

6. **DISTINCT** Из результирующего набора удаляются строки с повторяющимися значениями в столбцах, помеченных ключевым словом DISTINCT.

7. **ORDER BY** Если указано предложение ORDER BY, строки сортируются по заданным столбцам в возрастающем (ASC) или убывающем (DESC) порядке. Поскольку выражения из SELECT уже вычислены, здесь можно использовать их псевдонимы.

8. **LIMIT / OFFSET** На последнем этапе применяется ограничение количества возвращаемых строк. Строки, выходящие за пределы диапазона, заданного LIMIT и OFFSET, отбрасываются, и формируется итоговый результат запроса.

<p align="center">
  <img width="400" alt="sqlRUS" src="https://github.com/user-attachments/assets/30a2c09f-089d-4fdf-870e-20b9ac4623f6" />
</p>

---

Рисунок 9 иллюстрирует использование оператора INSERT для добавления данных в таблицу базы данных.

<p align="center">
  <img src="https://github.com/user-attachments/assets/f3fd3624-6786-4c16-b172-67198b550e8a" width="500" alt="Figure 9" />
  <br>
  <em><b>Рисунок 9. Оператор SQL INSERT</b></em>
</p>

Рисунок 10 иллюстрирует использование оператора UPDATE для изменения данных.

<p align="center">
  <img src="https://github.com/user-attachments/assets/57266ea8-b4ba-4e8d-8307-48da5bdfe8dd" width="500" alt="Figure 10" />
  <br>
  <em><b>Рисунок 10. Оператор SQL UPDATE</b></em>
</p>

Рисунок 11 иллюстрирует использование оператора DELETE для удаления данных.

<p align="center">
  <img src="https://github.com/user-attachments/assets/0c364a9d-0a70-4f9c-8b07-8bdd154bac8d" width="300" alt="Figure 11" />
  <br>
  <em><b>Рисунок 11. Оператор SQL DELETE</b></em>
</p>

Рисунок 12 иллюстрирует использование оператора CREATE TABLE.

<p align="center">
  <img src="https://github.com/user-attachments/assets/a78e84cf-78df-49ac-9d51-b9d242f913a5" width="600" alt="Figure 12" />
  <br>
  <em><b>Рисунок 12. Оператор SQL CREATE TABLE</b></em>
</p>

Рисунок 13 иллюстрирует использование ALTER TABLE ADD COLUMN.

<p align="center">
  <img src="https://github.com/user-attachments/assets/900d1960-bd06-493f-ad60-b54e3cae4dd7" width="500" alt="Figure 13" />
  <br>
  <em><b>Рисунок 13. ALTER TABLE ADD COLUMN</b></em>
</p>

Рисунок 14 иллюстрирует использование ALTER TABLE DROP COLUMN.

<p align="center">
  <img src="https://github.com/user-attachments/assets/1db93cd9-a9e2-45a0-9830-8a3410237e4d" width="300" alt="Figure 14" />
  <br>
  <em><b>Рисунок 14. ALTER TABLE DROP COLUMN</b></em>
</p>

Рисунок 15 иллюстрирует использование ALTER TABLE RENAME TO.

<p align="center">
  <img src="https://github.com/user-attachments/assets/dd6cb1c6-57fb-437a-a3f8-5a10dd0b7c74" width="300" alt="Figure 15" />
  <br>
  <em><b>Рисунок 15. ALTER TABLE RENAME TO</b></em>
</p>

Рисунок 16 иллюстрирует использование DROP TABLE.

<p align="center">
  <img src="https://github.com/user-attachments/assets/8ef0c5b9-e34c-499a-ab1e-2fdb6f00f896" width="300" alt="Figure 16" />
  <br>
  <em><b>Рисунок 16. Оператор SQL DROP TABLE</b></em>
</p>

# Secondary Memory Storage Engine Coursework

This repository contains two C assignments developed for an Information Organization and Retrieval course. The projects simulate how a database system stores records in secondary memory and uses indexes to reduce the number of disk accesses.

The code works with fixed-size in-memory strings that represent data files and index files. Operations are executed through SQL-like commands provided in input files.

## Projects

### T01 - Indexing

`T01` implements a small storage system backed by:

- Primary indexes for users, courses, and enrollments.
- Secondary indexes for course titles and enrollment dates.
- An inverted list for course categories.
- Logical deletion and compaction for user records.

The main goal is to show how sorted indexes and inverted lists can speed up search and listing operations over simulated secondary-memory files.

### T02 - B-Trees

`T02` evolves the indexing approach by replacing the sorted in-memory index arrays with serialized B-tree indexes.

It includes:

- B-tree insertion with node splitting and key promotion.
- B-tree search with path reporting.
- B-tree deletion with rebalancing.
- B-tree-backed primary and secondary indexes.
- An inverted list stored as fixed-size index records.

The assignment focuses on how tree indexes reduce access cost as the number of records grows.

## Repository Structure

```text
.
+-- T01/
|   +-- T01.c
|   +-- Makefile
|   +-- in/
|   +-- out/
+-- T02/
|   +-- T02.c
|   +-- Makefile
|   +-- in/
|   +-- out/
+-- README.md
```

## Build and Test

Run the provided test suite for each assignment:

```bash
cd T01
make
```

```bash
cd T02
make
```

The Makefiles compile the assignment and compare the generated outputs with the expected files in `out/`.

To remove generated files:

```bash
make clean
```

## Input Format

Each test file contains SQL-like commands interpreted by the assignment driver. Examples:

```sql
INSERT INTO usuarios VALUES ('00000000001', 'User Name', 'user@email.com', '99999999999');
SELECT * FROM usuarios WHERE id_usuario = '00000000001';
SELECT * FROM cursos ORDER BY id_curso ASC;
\echo index usuarios_idx
\q
```

## Notes

The `main` functions, record layouts, structs, constants, and command parser were provided as part of the course template. The implemented work focuses on the previously empty data manipulation, indexing, inverted-list, and B-tree functions.
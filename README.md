# Celestial Bodies Database

## Overview
The Celestial Bodies Database is a PostgreSQL database designed to store information about various celestial bodies, including galaxies, stars, planets, moons, and comets. This project is part of the FreeCodeCamp curriculum and aims to demonstrate the ability to create and manage a relational database with complex relationships.

## Database Schema
The database consists of the following tables:
- `galaxy`
- `star`
- `planet`
- `moon`
- `comet`

Each table has a primary key, various attributes, and foreign keys to establish relationships with other tables.

## Table Structure

### Galaxy Table
| Column                  | Data Type      | Constraints              |
|-------------------------|----------------|--------------------------|
| `galaxy_id`             | `SERIAL`       | Primary Key              |
| `name`                  | `VARCHAR(100)` | Unique, Not Null         |
| `description`           | `TEXT`         |                          |
| `age_in_millions_of_years` | `INT`       | Not Null                 |
| `distance_from_earth`   | `NUMERIC`      | Not Null                 |
| `has_life`              | `BOOLEAN`      | Not Null                 |

### Star Table
| Column                  | Data Type      | Constraints              |
|-------------------------|----------------|--------------------------|
| `star_id`               | `SERIAL`       | Primary Key              |
| `name`                  | `VARCHAR(100)` | Unique, Not Null         |
| `type`                  | `VARCHAR(50)`  |                          |
| `mass`                  | `NUMERIC`      | Not Null                 |
| `is_visible`            | `BOOLEAN`      | Not Null                 |
| `galaxy_id`             | `INT`          | Foreign Key (galaxy_id)  |

### Planet Table
| Column                  | Data Type      | Constraints              |
|-------------------------|----------------|--------------------------|
| `planet_id`             | `SERIAL`       | Primary Key              |
| `name`                  | `VARCHAR(100)` | Unique, Not Null         |
| `type`                  | `VARCHAR(50)`  |                          |
| `radius`                | `INT`          | Not Null                 |
| `has_life`              | `BOOLEAN`      | Not Null                 |
| `star_id`               | `INT`          | Foreign Key (star_id)    |

### Moon Table
| Column                  | Data Type      | Constraints              |
|-------------------------|----------------|--------------------------|
| `moon_id`               | `SERIAL`       | Primary Key              |
| `name`                  | `VARCHAR(100)` | Unique, Not Null         |
| `radius`                | `INT`          | Not Null                 |
| `has_water`             | `BOOLEAN`      | Not Null                 |
| `planet_id`             | `INT`          | Foreign Key (planet_id)  |

### Comet Table
| Column                  | Data Type      | Constraints              |
|-------------------------|----------------|--------------------------|
| `comet_id`              | `SERIAL`       | Primary Key              |
| `name`                  | `VARCHAR(100)` | Unique, Not Null         |
| `composition`           | `TEXT`         |                          |
| `orbit_period`          | `INT`          | Not Null                 |
| `is_periodic`           | `BOOLEAN`      | Not Null                 |

## Data Insertion
The database is populated with sample data for each table to demonstrate its functionality. Here are some examples of the data:

### Galaxy Table
```sql
INSERT INTO galaxy (name, description, age_in_millions_of_years, distance_from_earth, has_life)
VALUES
('Milky Way', 'Our galaxy', 13600, 0, TRUE),
('Andromeda', 'Nearest large galaxy', 10000, 2537000, FALSE),
('Sombrero', 'Galaxy with a bright nucleus', 11000, 29000000, FALSE),
('Whirlpool', 'Interacting grand-design spiral galaxy', 500, 23000000, FALSE),
('Black Eye', 'Galaxy with dark band of absorbing dust', 1000, 17000000, FALSE),
('Pinwheel', 'Face-on spiral galaxy', 14000, 21000000, FALSE);
```
### Star Table
```sql
INSERT INTO star (name, type, mass, is_visible, galaxy_id)
VALUES
('Sun', 'G-type main-sequence star', 1.989, TRUE, 1),
('Betelgeuse', 'Red supergiant', 20.0, TRUE, 1),
('Sirius', 'Binary star', 2.063, TRUE, 1),
('Alpha Centauri', 'Triple star', 2.188, TRUE, 1),
('Proxima Centauri', 'Red dwarf', 0.123, TRUE, 1),
('Rigel', 'Blue supergiant', 21.0, TRUE, 1);
```
### Planet
```sql
INSERT INTO planet (name, type, radius, has_life, star_id)
VALUES
('Earth', 'Terrestrial', 6371, TRUE, 1),
('Mars', 'Terrestrial', 3390, FALSE, 1),
('Jupiter', 'Gas giant', 69911, FALSE, 1),
('Saturn', 'Gas giant', 58232, FALSE, 1),
('Uranus', 'Ice giant', 25362, FALSE, 1),
('Neptune', 'Ice giant', 24622, FALSE, 1),
('Proxima b', 'Exoplanet', 7160, FALSE, 5),
('Alpha Centauri Bb', 'Exoplanet', 7160, FALSE, 4),
('Kepler-22b', 'Exoplanet', 12700, FALSE, 3),
('Gliese 581g', 'Exoplanet', 7160, FALSE, 4),
('HD 209458 b', 'Exoplanet', 7160, FALSE, 2),
('Kepler-452b', 'Exoplanet', 12700, FALSE, 3);
```

### Moon Table 
```sql
INSERT INTO moon (name, radius, has_water, planet_id)
VALUES
('Moon', 1737, FALSE, 1),
('Phobos', 11, FALSE, 2),
('Deimos', 6, FALSE, 2),
('Io', 1821, FALSE, 3),
('Europa', 1560, TRUE, 3),
('Ganymede', 2634, TRUE, 3),
('Callisto', 2410, TRUE, 3),
('Titan', 2575, TRUE, 4),
('Rhea', 764, FALSE, 4),
('Iapetus', 735, FALSE, 4),
('Dione', 561, FALSE, 4),
('Tethys', 531, FALSE, 4),
('Enceladus', 252, TRUE, 4),
('Miranda', 235, FALSE, 5),
('Ariel', 578, TRUE, 5),
('Umbriel', 584, FALSE, 5),
('Titania', 789, FALSE, 5),
('Oberon', 761, FALSE, 5),
('Triton', 1353, TRUE, 6),
('Nereid', 170, FALSE, 6);
```
### Comet Table
```sql
INSERT INTO comet (name, composition, orbit_period, is_periodic)
VALUES
('Halley', 'Rock and ice', 76, TRUE),
('Hale-Bopp', 'Dust and gas', 2533, FALSE),
('Encke', 'Dust and gas', 3.3, TRUE);
```

## How to Use
```bash
git clone https://github.com/yourusername/celestial-bodies-database.git
cd celestial-bodies-database
```

```bash
psql -U postgres < universe.sql
```

```bash
psql --username=freecodecamp --dbname=universe

```

```sql
SELECT * FROM galaxy;
SELECT * FROM star;
SELECT * FROM planet;
SELECT * FROM moon;
SELECT * FROM comet;
```







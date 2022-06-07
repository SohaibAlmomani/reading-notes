# Reading-Notes.

# sequelize-normalization-associations :

Sequelize supports the standard associations: One-To-One, One-To-Many and Many-To-Many.

Sequelize provides four types of associations that should be combined to create them:

- The HasOne association
- The BelongsTo association
- The HasMany association
- The BelongsToMany association

> ## Defining the Sequelize associations :

Telling Sequelize that you want an association between the two needs (A and B) just a function call:

```js
const A = sequelize.define("A" /* ... */);
const B = sequelize.define("B" /* ... */);

A.hasOne(B); // A HasOne B
A.belongsTo(B); // A BelongsTo B
A.hasMany(B); // A HasMany B
A.belongsToMany(B, { through: "C" }); // A BelongsToMany B through the junction table C
```

`A` ==> called the source model.

`B` ==> called the target model.

They all accept an options object as a second parameter (optional for the first three, mandatory for belongsToMany containing at least the through property):

```js
A.hasOne(B, {
  /* options */
});
A.belongsTo(B, {
  /* options */
});
A.hasMany(B, {
  /* options */
});
A.belongsToMany(B, { through: "C" /* options */ });
```

- The `A.hasOne(B)` association means that a `One-To-One` relationship exists between `A and B`, with the foreign key being defined in the target `model (B)`.

- The `A.belongsTo(B)` association means that a `One-To-One` relationship exists between `A and B`, with the foreign key being defined in the source `model (A)`.

- The `A.hasMany(B)` association means that a `One-To-Many` relationship exists between `A and B`, with the foreign key being defined in the target `model (B)`.

# Creating the standard relationships :

- To create a One-To-One relationship, the hasOne and belongsTo associations are used together;

- To create a One-To-Many relationship, the hasMany and belongsTo associations are used together;

- To create a Many-To-Many relationship, two belongsToMany calls are used together.

> ## One-To-One relationships :

let's assume that we have two models, Foo and Bar. We want to setup a One-To-One relationship between them such that Bar gets a fooId column.

```js
Foo.hasOne(Bar);
Bar.belongsTo(Foo);
```

This way, calling Bar.sync() after the above will yield the following SQL (on PostgreSQL, for example):

```js
CREATE TABLE IF NOT EXISTS "foos" (
  /* ... */
);
CREATE TABLE IF NOT EXISTS "bars" (
  /* ... */
  "fooId" INTEGER REFERENCES "foos" ("id") ON DELETE SET NULL ON UPDATE CASCADE
  /* ... */
);
```

## Options :

Delete and onUpdate

```js
Foo.hasOne(Bar, {
  onDelete: "RESTRICT",
  onUpdate: "RESTRICT",
});
Bar.belongsTo(Foo);
```

### Customizing the foreign key

```js
// Option 1
Foo.hasOne(Bar, {
  foreignKey: "myFooId",
});
Bar.belongsTo(Foo);

// Option 2
Foo.hasOne(Bar, {
  foreignKey: {
    name: "myFooId",
  },
});
Bar.belongsTo(Foo);

// Option 3
Foo.hasOne(Bar);
Bar.belongsTo(Foo, {
  foreignKey: "myFooId",
});

// Option 4
Foo.hasOne(Bar);
Bar.belongsTo(Foo, {
  foreignKey: {
    name: "myFooId",
  },
});
```

### Special methods

```js
Foo.hasOne(Bar);

-fooInstance.getBar();
-fooInstance.setBar();
-fooInstance.createBar();
```

> ## One-To-Many relationships :

### Goal :

we have the models Team and Player. We want to tell Sequelize that there is a One-To-Many relationship between them, meaning that one Team has many Players, while each Player belongs to a single Team.

```js
Team.hasMany(Player);
Player.belongsTo(Team);
```

In PostgreSQL the above setup will yield the following SQL upon sync():

```js
CREATE TABLE IF NOT EXISTS "Teams" (
  /* ... */
);
CREATE TABLE IF NOT EXISTS "Players" (
  /* ... */
  "TeamId" INTEGER REFERENCES "Teams" ("id") ON DELETE SET NULL ON UPDATE CASCADE,
  /* ... */
);
```

## Options :

To change the name of the foreign key and make sure that the relationship is mandatory, we can do :

```js
Team.hasMany(Player, {
  foreignKey: "clubId",
});
Player.belongsTo(Team);
```

Like One-To-One relationships, `ON DELETE` defaults to `SET NULL` and `ON UPDATE` defaults to `CASCADE`.

### Special methods

```js
Foo.belongsTo(Bar);

-fooInstance.getBar();
-fooInstance.setBar();
-fooInstance.createBar();
```

> ## Many-To-Many relationships :

### Goal :

we will consider the models `Movie` and `Actor`. One actor may have participated in many movies, and one movie had many actors involved with its production. The junction table that will keep track of the associations will be called `ActorMovies`, which will contain the foreign keys `movieId` and `actorId`.

```js
const Movie = sequelize.define("Movie", { name: DataTypes.STRING });
const Actor = sequelize.define("Actor", { name: DataTypes.STRING });
Movie.belongsToMany(Actor, { through: "ActorMovies" });
Actor.belongsToMany(Movie, { through: "ActorMovies" });
```

Since a string was given in the through option of the `belongsToMany` call, Sequelize will automatically create the `ActorMovies` model which will act as the --junction model--.

In PostgreSQL :

```js
CREATE TABLE IF NOT EXISTS "ActorMovies" (
  "createdAt" TIMESTAMP WITH TIME ZONE NOT NULL,
  "updatedAt" TIMESTAMP WITH TIME ZONE NOT NULL,
  "MovieId" INTEGER REFERENCES "Movies" ("id") ON DELETE CASCADE ON UPDATE CASCADE,
  "ActorId" INTEGER REFERENCES "Actors" ("id") ON DELETE CASCADE ON UPDATE CASCADE,
  PRIMARY KEY ("MovieId","ActorId")
);
```

Instead of a string, passing a model directly is also supported, and in that case the given model will be used as the junction model(and no model will be created automatically).

```js
const Movie = sequelize.define("Movie", { name: DataTypes.STRING });
const Actor = sequelize.define("Actor", { name: DataTypes.STRING });
const ActorMovies = sequelize.define("ActorMovies", {
  MovieId: {
    type: DataTypes.INTEGER,
    references: {
      model: Movie, // 'Movies' would also work
      key: "id",
    },
  },
  ActorId: {
    type: DataTypes.INTEGER,
    references: {
      model: Actor, // 'Actors' would also work
      key: "id",
    },
  },
});
Movie.belongsToMany(Actor, { through: ActorMovies });
Actor.belongsToMany(Movie, { through: ActorMovies });
```

### Speciol method :

```js
Foo.belongsToMany(Bar, { through: Baz });

-fooInstance.getBars();
-fooInstance.countBars();
-fooInstance.hasBar();
-fooInstance.setBars();
-fooInstance.addBar();
-fooInstance.removeBar();
-fooInstance.createBar();
```

- Why associations are defined in pairs?

  - To create a One-To-One relationship, the hasOne and belongsTo associations are used together;
  - To create a One-To-Many relationship, the hasMany and belongsTo associations are used together;
  - To create a Many-To-Many relationship, two belongsToMany calls are used together.

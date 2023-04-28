Steps

npm install sequelize sequelize-cli pg pg-hstore

npx sequelize-cli

npx sequelize-cli model:generate --name {model name} --attributes title:string,content:text,userId:integer

change to this format - ex:

```javascript
module.exports = (sequelize, DataTypes) => {
const User = sequelize.define('User', {
name: DataTypes.STRING,
email: DataTypes.STRING
}, {});
User.associate = function(models) {
// associations can be defined here
User.hasMany(models.Post, {
foreignKey: 'userId',
as: 'posts',
onDelete: 'CASCADE',
});

    User.hasMany(models.Comment, {
      foreignKey: 'userId',
      as: 'comments',
      onDelete: 'CASCADE',
    });

};
return User;
};

npx sequelize-cli seed:generate --name {model name}

npx sequelize-cli db:migrate

npx sequelize-cli db:migrate:undo:all
```

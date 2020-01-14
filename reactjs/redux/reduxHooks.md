# 🏒Redux Hooks

```javascript
const Profile = props => {
  const dispatch = useDispatch();
  const profile = useSelector(store => store.example.profile);

  // update id
  const updateId = () => {
    dispatch(updateExampleProfile({ id: "test" }));
  };

  // update id twice
  const updateId2 = () => {
    dispatch(updateExampleProfile({ id: "test2" }));
  };

  return (
    <div>
      <h1>useState, useEffect Example</h1>
      Profile! <br />
      ID: {profile.id} <br />
      ButtonClick Count is: {counter} <br />
      <button onClick={updateId}>Update profile</button>
      <button onClick={updateId2}>Update profile</button>
    </div>
  );
};
```

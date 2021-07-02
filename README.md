# reactBirthdayReminderApp
This React application takes in data and uses it to create a list which keeps track of birthdays.



Data in the form of an array of objects is supplied (or could be fetched) and imported into App.js where state is used upon it to monitor the data. Some of that data is then used to populate the page. The onClick() will empty the array of data objects.
```React
function App() {
  const [people, setPeople] = useState(data);
  return (
    <main>
      <section className="container">
        <h3>{people.length} birthdays today</h3>
        <List people={people} />
        <button onClick={() => setPeople([])}>Clear All</button>
      </section>
    </main>
  );
}
```

The <List /> element brings in the data from the array of objects as a prop so it can be used in the Data.jsx file. The array is then mapped over and deconstructed so that its properties can be set dynamically.
```React
const List = ({ people }) => {
  return (
    <>
      {people.map((person) => {
        const { id, name, age, image } = person;
        return (
          <article key={id} className="person">
            <img src={image} alt={name} />
            <div>
              <h4>{name}</h4>
              <p>{age} year</p>
            </div>
          </article>
        );
      })}
    </>
  );
};
```

Then render.
```React
ReactDOM.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
  document.getElementById('root')
);
```

***End walkthrough

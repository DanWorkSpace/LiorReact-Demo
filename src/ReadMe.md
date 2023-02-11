import React from "react";
import ReactDOM from "react-dom";
import Client from "./Client";
import ClientForm from "./ClientForm";

import "./styles.css";

class App extends React.Component {
// state of the component :: state is an object
//containe data of our component

// reference : create a ref from the DOM => cliInput = React.createRef(); and remove => ref={this.cliInput} from the input

state = {
Rclients: [
{ id: 1, nam: "Dan Worker" },
{ id: 2, nam: "Youssef Azzekh" },
{ id: 3, nam: "Toughmari Moh" }
],
NewCli: ""
//compteur: 0
};

onClickDelete = (id) => {
// console.log(id);
// const Clients = this.state.Rclients.slice();
const Rclients = [...this.state.Rclients];

    const index = Rclients.findIndex((Rclients) => Rclients.id === id);

    Rclients.splice(index, 1);

    // this.setState({ Rclients: Clients });
    this.setState({ Rclients });

};

handleSubmit = (event) => {
event.preventDefault();
// console.log("It's Work !");
// console.log(this.cliInput.current.value);

    const id = new Date().getTime();
    const nam = this.state.NewCli;

    // const Client = { id: id, nam: nam };
    // const Client = { id, nam };

    // const Clients = this.state.Rclients.slice();
    const Clients = [...this.state.Rclients];

    // Clients.push(Client);
    Clients.push({ id, nam });

    this.setState({ Rclients: Clients, NewCli: "" });

};

handleChange = (event) => {
// const val = event.currentTarget.value;
this.setState({ NewCli: event.currentTarget.value });
//console.log(event.currentTarget.value);
};

/_handleClick = () => {
// this.state.compteur++; setState come from React.Component
// this.setState({ compteur: this.state.compteur + 1 });
// console.log(this.state);
const cli = this.state.Rclients.slice();
cli.push({ id: 4, nam: "Simo PHP Dev" });
this.setState({ Rclients: cli });
};_/

// code JSX start from render()
// the interpolation of JSX of the const title is
// const title = "React-JS"; ==> {title}
render() {
const title = "React-JS";
const element = <li>D'ont forget the Chahada</li>;
/_const ArrayElement = [
<li>D'ont trust Any Body</li>,
<li>D'ont trust Any Body</li>,
<li>D'ont trust Any Body</li>
];_/
/_const ArrayElements = this.state.Rclients.map(function (Rclients) {
// function map() in React : create a table of data that will transform to another data
// Boucle to this Rclents and create a new one to result of transfer of this data in the table Rclients
return (
<li>
{Rclients.nam}
<button>X</button>
</li>
);
});_/

    /*const ArrayElements = this.state.Rclients.map((Rclients) => (
      <li>
        {Rclients.nam}
        <button>X</button>
      </li>
    ));*/

    // when we want o made a loop to a table we execute the maap
    // fx to a table => this.state.Rclients.map((Rclients)
    // so we have that return based of the state of the data existing in the state

    // Integrate with evenments of the users

    /*handleClick(){
      alert("Hi Dev React-JS")
      // this fx d'ont work at all and we call
    }

    handleClick(){
      console.log(this.state);
      // undefinde :: this is not represent at all our component :: onClick={this.handleClick}
      // 1- when we want to resolve this error :: onClick={this.handleClick.bind(this)} => console.log(this.state);
      // 2- () => this.handleClick() flech fx to ask for the handleClick fx => console.log(this.state);
      // 3- handleClick = () => {
      console.log(this.state);
    }; =>  onClick={this.handleClick}>

      {this.state.compteur}
      <button onClick={this.handleClick}>Click Me</button>

    }*/

    return (
      <div>
        <h1>React : 1 Houre of Understunding the laibrery</h1>
        <h3>Students : Want to learn {title}</h3>
        <h4>{element}</h4>
        <ul>
          {this.state.Rclients.map((Rclients) => (
            <Client details={Rclients} onDelete={this.onClickDelete} />
          ))}
        </ul>
        <ClientForm />
      </div>
    );

}
}

const rootElement = document.getElementById("root");
ReactDOM.render(<App />, rootElement);

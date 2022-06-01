```

import React, { Component } from "react";
import { render } from "@testing-library/react";
import night from "./night.jpg";
import { Image } from "react-bootstrap";
import { Carousel } from "react-bootstrap";
import home from "./home.jpg";

export default class Home extends Component {
  render() {
    var background = { backgroundSize: "cover" };
    var textStyle = {
      position: "absolute",
      top: "50%",
      left: "50%",
      color: "purple"
    };
    return (
      <div style={{ width: "auto" }}>
        <Image
          style={background}
          responsive="true"
          src={require("./home.jpg")}
          width="1348px"
          height="600px"
        ></Image>

        <div>
          <h1>&nbsp;</h1>
          <h1 align="center">TESTIMONIALS</h1>
          <h1>&nbsp;</h1>
          <Carousel>
            <Carousel.Item>
              <img
                className="d-block w-100"
                src="https://images.squarespace-cdn.com/content/v1/54d13b45e4b0f90e6ca28168/1510072845364-O01E2MIJBTWCJ3N03VXP/ke17ZwdGBToddI8pDm48kDONSgQXwBYB20AZSG99sXx7gQa3H78H3Y0txjaiv_0fDoOvxcdMmMKkDsyUqMSsMWxHk725yiiHCCLfrh8O1z4YTzHvnKhyp6Da-NYroOW3ZGjoBKy3azqku80C789l0hReLB75oIvKxcDxwlnLXaanQ4b7g0mjR1pPNaLl5krdG6DE4mXhsDJSK2uJyqajoA/Loop+Test_021117_mike37405.jpg?format=1500w"
                alt="First slide"
              />
              <Carousel.Caption>
                <h1>Jimmy John</h1>
                <p>
                  "I love this website! It has changed the way I sublease my
                  apartment and I will never stop using it."
                </p>
              </Carousel.Caption>
            </Carousel.Item>
            <Carousel.Item>
              <img
                className="d-block w-100"
                src="https://www.shutterstock.com/blog/wp-content/uploads/sites/5/2017/12/4-6.jpg"
                alt="Third slide"
              />

              <Carousel.Caption>
                <h1>Carole Baskin</h1>
                <p>
                  "I was able to find the perfect location and apartment to
                  sublease with ease. Thanks BINZ!"
                </p>
              </Carousel.Caption>
            </Carousel.Item>
            <Carousel.Item>
              <img
                className="d-block w-100"
                src="https://images.squarespace-cdn.com/content/v1/5bc59bceb9144953e7a030d1/1543232682025-S6YOSHRDZFPN13EC230M/ke17ZwdGBToddI8pDm48kLkXF2pIyv_F2eUT9F60jBl7gQa3H78H3Y0txjaiv_0fDoOvxcdMmMKkDsyUqMSsMWxHk725yiiHCCLfrh8O1z4YTzHvnKhyp6Da-NYroOW3ZGjoBKy3azqku80C789l0iyqMbMesKd95J-X4EagrgU9L3Sa3U8cogeb0tjXbfawd0urKshkc5MgdBeJmALQKw/EmptyName+61+copy.jpg?format=1000w"
                alt="Third slide"
              />

              <Carousel.Caption>
                <h1>Joseph Allen</h1>
                <p>
                  "I cannot believe I went this long without this website. It is
                  amazing and it makes subleasing very simple."
                </p>
              </Carousel.Caption>
            </Carousel.Item>
          </Carousel>
          ;
        </div>
      </div>
    );
  }
}


```

#### Create 


```
import React, { Component } from "react";
import axios from "axios";
import { render } from "@testing-library/react";

export default class Create extends Component {
  constructor(props) {
    super(props);
    this.onChangeName = this.onChangeName.bind(this);
    this.onChangePhone = this.onChangePhone.bind(this);
    this.onChangeEmail = this.onChangeEmail.bind(this);
    this.onChangeDuration = this.onChangeDuration.bind(this);
    this.onChangeRent = this.onChangeRent.bind(this);
    this.onChangeLocation = this.onChangeLocation.bind(this);
    this.onChangePets = this.onChangePets.bind(this);
    this.onChangeFurnished = this.onChangeFurnished.bind(this);
    this.onChangeStartDate = this.onChangeStartDate.bind(this);
    this.onChangeEndDate = this.onChangeEndDate.bind(this);
    this.onChangeComments = this.onChangeComments.bind(this);
    this.onChangeFile = this.onChangeFile.bind(this);
    this.onSubmit = this.onSubmit.bind(this);
    this.state = {
      name: "",
      phone: 0,
      email: "",
      duration: "",
      rentPerMonth: 0,
      location: "",
      pets: false,
      furnished: false,
      startDate: "",
      endDate: "",
      comments: "",
      file: "",
      fileName: ""
    };
  }

  componentDidMount() {
    if (!this.props.loggedIn) {
      this.props.history.push("/signin");
    }
  }

  onChangeName(e) {
    this.setState({
      name: e.target.value
    });
  }
  onChangePhone(e) {
    this.setState({
      phone: e.target.value
    });
  }
  onChangeEmail(e) {
    this.setState({
      email: e.target.value
    });
  }
  onChangeDuration(e) {
    this.setState({
      duration: e.target.value
    });
  }
  onChangeRent(e) {
    this.setState({
      rent: e.target.value
    });
  }
  onChangeLocation(e) {
    this.setState({
      location: e.target.value
    });
  }
  onChangePets(e) {
    this.setState({
      pets: e.target.value
    });
  }
  onChangeFurnished(e) {
    this.setState({
      furnished: e.target.value
    });
  }
  onChangeStartDate(e) {
    this.setState({
      startDate: e.target.value
    });
  }
  onChangeEndDate(e) {
    this.setState({
      endDate: e.target.value
    });
  }
  onChangeComments(e) {
    this.setState({
      comments: e.target.value
    });
  }
  onChangeFile(e) {
    this.setState({
      file: e.target.files[0],
      fileName: e.target.files[0].name
    });
  }

  async onSubmit(e) {
    e.preventDefault();
    const formData = new FormData();
    formData.append("name", this.state.name);
    formData.append("phone", this.state.phone);
    formData.append("email", this.state.email);
    formData.append("duration", this.state.duration);
    formData.append("rentPerMonth", this.state.rent);
    formData.append("location", this.state.location);
    formData.append("pets", this.state.pets === "Yes" ? true : false);
    formData.append("furnished", this.state.furnished === "Yes" ? true : false);
    formData.append("startDate", this.state.startDate);
    formData.append("endDate", this.state.endDate);
    formData.append("comments", this.state.comments);
    formData.append("listingImage", this.state.file);
    formData.append("token", localStorage.getItem("token"));

    console.log("Form submitted:");
    console.log(`Name: ${this.state.name}`);
    console.log(`Phone: ${this.state.phone}`);
    console.log(`Email: ${this.state.email}`);
    console.log(`Duration: ${this.state.duration}`);
    console.log(`Rent Per Month: ${this.state.rent}`);
    console.log(`Location: ${this.state.location}`);
    console.log(`Peys: ${this.state.pets}`);
    console.log(`Furnished: ${this.state.furnished}`);
    console.log(`Start Date: ${this.state.startDate}`);
    console.log(`End Date: ${this.state.endDate}`);
    console.log(`Comments: ${this.state.comments}`);
    console.log(`File: ${this.state.file}`);
    console.log(`File Name: ${this.state.fileName}`);

    const response = await axios.post(
      "http://localhost:8080/listings",
      formData,
      {
        headers: {
          "Content-Type": "multipart/form-data"
        }
      }
    );

    console.log(response.data);

    this.props.history.push(`/listings/${response.data.id}`);
  }
  render() {
    return (
      <div style={{ marginTop: 20 }}>
        <h3>Create New Listing</h3>
        <form onSubmit={this.onSubmit}>
          <div className="form-group">
            <label>Name: </label>
            <input
              type="text"
              required
              className="form-control"
              value={this.state.name}
              onChange={this.onChangeName}
            />
          </div>

          <div className="form-group">
            <label>Phone: </label>
            <input
              type="text"
              required
              className="form-control"
              value={this.state.phone}
              onChange={this.onChangePhone}
            />
          </div>

          <div className="form-group">
            <label>Email: </label>
            <input
              type="text"
              required
              className="form-control"
              value={this.state.email}
              onChange={this.onChangeEmail}
            />
          </div>

          <div className="form-group">
            <label>Rent Per Month: </label>
            <input
              type="text"
              required
              className="form-control"
              value={this.state.rent}
              onChange={this.onChangeRent}
            />
          </div>

          <div className="form-group">
            <label>Location: </label>
            <input
              type="text"
              required
              className="form-control"
              value={this.state.location}
              onChange={this.onChangeLocation}
            />
          </div>

          <div className="form-group">
            <label>Pets: </label>
            <div className="form-check form-check-inline">
              <input
                className="form-check-input"
                type="radio"
                required
                name="petsOptions"
                id="noPets"
                value="No"
                checked={this.state.pets == "No"}
                onChange={this.onChangePets}
              />
              <label className="form-checl-label">No Pets</label>
            </div>
            <div className="form-check form-check-inline">
              <input
                className="form-check-input"
                type="radio"
                required
                name="petsOptions"
                id="yesPets"
                value="Yes"
                checked={this.state.pets == "Yes"}
                onChange={this.onChangePets}
              />
              <label className="form-checl-label">Can Have Pets</label>
            </div>
          </div>

          <div className="form-group">
            <label>Furnished: </label>
            <div className="form-check form-check-inline">
              <input
                className="form-check-input"
                type="radio"
                required
                name="furnishedOptions"
                id="Furnished"
                value="Yes"
                checked={this.state.furnished == "Yes"}
                onChange={this.onChangeFurnished}
              />
              <label className="form-checl-label">Furnished</label>
            </div>
            <div className="form-check form-check-inline">
              <input
                className="form-check-input"
                type="radio"
                required
                name="furnishedOptions"
                id="NotFurnished"
                value="No"
                checked={this.state.furnished == "No"}
                onChange={this.onChangeFurnished}
              />
              <label className="form-checl-label">Not Furnished</label>
            </div>
          </div>

          <div className="form-group">
            <label>Start Date: </label>
            <input
              type="date"
              required
              className="form-control"
              value={this.state.startDate}
              onChange={this.onChangeStartDate}
            />
          </div>

          <div className="form-group">
            <label>End Date: </label>
            <input
              type="date"
              required
              className="form-control"
              value={this.state.endDate}
              onChange={this.onChangeEndDate}
            />
          </div>

          <div className="form-group">
            <label>Comments: </label>
            <input
              type="text"
              required
              className="form-control"
              value={this.state.comments}
              onChange={this.onChangeComments}
            />
          </div>

          <div className="form-group">
            <label htmlFor="exampleFormControlFile1">Pictures</label>
            <input
              type="file"
              required
              className="form-control-file"
              id="exampleFormControlFile1"
              onChange={this.onChangeFile}
            ></input>
          </div>

          <div className="form-group">
            <button
              onClick={this.onNavigateListings}
              className="btn btn-primary"
            >
              Submit
            </button>
          </div>
        </form>
      </div>
    );
  }
}

```


#### Login


```

import React, { Component } from "react";
import { render } from "@testing-library/react";
import axios from "axios";

export default class SignIn extends Component {
  state = {
    email: "",
    password: "",
    showFailed: false
  };

  onChangeEmail = e => {
    this.setState({ email: e.target.value, showFailed: false });
  };

  onChangePassword = e => {
    this.setState({ password: e.target.value, showFailed: false });
  };

  onSubmit = async e => {
    e.preventDefault();

    const response = await axios.post("http://localhost:8080/users/login", {
      email: this.state.email,
      password: this.state.password
    });

    if (response.data.success) {
      this.props.onLogin(response.data.token);
      this.props.history.push("/profile");
    } else {
      this.setState({ showFailed: true });
    }
  };

  render() {
    return (
      <div style={({ marginTop: 20 }, { marginLeft: 20 })}>
        <h3>Sign In</h3>
        {this.state.showFailed && <div>Login failed!</div>}
        <form onSubmit={this.onSubmit}>
          <div className="form-group">
            <label>Email: </label>
            <input
              type="text"
              className="form-control"
              value={this.state.email}
              onChange={this.onChangeEmail}
              style={{ width: "400px" }}
              required
            />
          </div>

          <div className="form-group">
            <label>Password: </label>
            <input
              type="password"
              className="form-control"
              value={this.state.password}
              onChange={this.onChangePassword}
              style={{ width: "400px" }}
              required
            />
          </div>

          <div className="form-group">
            <button className="btn btn-primary" style={{ width: "400px" }}>
              Sign In
            </button>
          </div>
        </form>
      </div>
    );
  }
}

```


#### Sign Up


```

import React, { Component } from "react";
import axios from "axios";
import { render } from "@testing-library/react";

export default class SignUp extends Component {
  constructor(props) {
    super(props);
    this.onChangeEmail = this.onChangeEmail.bind(this);
    this.onChangeName = this.onChangeName.bind(this);
    this.onChangePassword = this.onChangePassword.bind(this);
    this.onChangeConfirmPassword = this.onChangeConfirmPassword.bind(this);
    this.onSubmit = this.onSubmit.bind(this);

    this.state = {
      email: "",
      name: "",
      password: "",
      confirmPassword: "",
      showConfirmError: false
    };
  }

  onChangeEmail(e) {
    this.setState({
      email: e.target.value
    });
  }

  onChangeName(e) {
    this.setState({
      name: e.target.value
    });
  }

  onChangePassword(e) {
    this.setState({
      password: e.target.value,
      showConfirmError: false
    });
  }

  onChangeConfirmPassword(e) {
    this.setState({
      confirmPassword: e.target.value,
      showConfirmError: false
    });
  }

  async onSubmit(e) {
    e.preventDefault();

    if (this.state.password !== this.state.confirmPassword) {
      this.setState({ showConfirmError: true });
      return;
    }

    console.log("Form submitted:");
    console.log(`Name: ${this.state.name}`);
    console.log(`Email: ${this.state.email}`);
    console.log(`Password: ${this.state.password}`);

    const response = await axios.post("http://localhost:8080/users", {
      name: this.state.name,
      email: this.state.email,
      password: this.state.password
    });

    console.log(response.data);

    this.props.onLogin(response.data.token);

    this.setState({
      email: "",
      password: ""
    });

    this.props.history.push("/profile");
  }

  render() {
    return (
      <div style={({ marginTop: 20 }, { marginLeft: 20 })}>
        <h3>Sign Up</h3>
        <form onSubmit={this.onSubmit}>
          <div className="form-group">
            <label>Name: </label>
            <input
              type="text"
              className="form-control"
              value={this.state.name}
              onChange={this.onChangeName}
              style={{ width: "400px" }}
            />
          </div>
          <div className="form-group">
            <label>Email: </label>
            <input
              type="text"
              className="form-control"
              value={this.state.email}
              onChange={this.onChangeEmail}
              style={{ width: "400px" }}
            />
          </div>

          <div className="form-group">
            <label>Password: </label>
            <input
              type="password"
              className="form-control"
              value={this.state.password}
              onChange={this.onChangePassword}
              style={{ width: "400px" }}
            />
          </div>
          <div className="form-group">
            <label>Confirm Password:</label>
            <input
              type="password"
              className="form-control"
              style={{ width: "400px" }}
              value={this.state.confirmPassword}
              onChange={this.onChangeConfirmPassword}
            ></input>
          </div>
          {this.state.showConfirmError && <div>Passwords do not match!</div>}

          <div className="form-group">
            <button className="btn btn-primary" style={{ width: "400px" }}>
              Sign Up
            </button>
          </div>
        </form>
      </div>
    );
  }
}

/*
import React, { Component } from "react";
import axios from "axios";
import { render } from "@testing-library/react";
export default class SignUp extends Component {
  constructor(props) {
    super(props);
    this.onChangeEmail = this.onChangeEmail.bind(this);
    this.onChangePassword = this.onChangePassword.bind(this);
    this.onSubmit = this.onSubmit.bind(this);
    this.state = {
      email: "",
      password: ""
    };
  }
  onChangeEmail(e) {
    this.setState({
      email: e.target.value
    });
  }
  onChangePassword(e) {
    this.setState({
      password: e.target.value
    });
  }
  async onSubmit(e) {
    e.preventDefault();
    const formData = new FormData();
    formData.append("email", this.state.email);
    formData.append("password", this.state.password);
    console.log("Form submitted:");
    console.log(`Email: ${this.state.email}`);
    console.log(`Password: ${this.state.password}`);
    const response = await axios.post(
      "http://localhost:8080/users",
      formData,
      {
        headers: {
          "Content-Type": "multipart/form-data"
        }
      }
    );
    console.log(response.data);
    this.setState({
      email: "",
      password: ""
    });
  }
  render() {
    return (
      <div style={{ marginTop: 20 }}>
        <h3>Sign Up</h3>
        <form onSubmit={this.onSubmit}>
          <div className="form-group">
            <label>Email: </label>
            <input
              type="text"
              className="form-control"
              value={this.state.email}
              onChange={this.onChangeEmail}
            />
          </div>
          <div className="form-group">
            <label>Password: </label>
            <input
              type="text"
              className="form-control"
              value={this.state.password}
              onChange={this.onChangePassword}
            />
          </div>
          <div className="form-group">
          <button
              onClick={this.onNavigateUsers}
              className="btn btn-primary"
            >
              Sign In
            </button>
          </div>
        </form>
      </div>
    );
  }
}
*/


```


#### About Us


```
import React, { Component } from "react";
import CardDeck from "react-bootstrap/CardDeck";
import Card from "react-bootstrap/Card";
export default class About extends Component {
  render() {
    return (
      <div>
        <h1 align="middle"> &nbsp;</h1>
        <h1 align="middle">ABOUT US</h1>
        <h4 align="middle">
          {" "}
          <font color="black">
            Finding safe and afforable housing near campus can be challenging.
            So we created a place where UNCC students can sub-lease their next
            home.
          </font>
        </h4>
        <h1 align="middle"> &nbsp;</h1>
        <CardDeck>
          <Card>
            <Card.Img
              variant="top"
              src="https://i.pinimg.com/originals/9d/aa/a2/9daaa251f5d00c224af2368a4dd185a9.jpg"
            />
            <Card.Body>
              <Card.Title>Harika Jampani</Card.Title>
              <Card.Text>
                Harika loves computer science. She is one of our Frontend
                developers. She is also a part of our design team.
              </Card.Text>
            </Card.Body>
            <Card.Footer>
              <small className="text-muted">Last updated 3 mins ago</small>
            </Card.Footer>
          </Card>
          <Card>
            <Card.Img
              variant="top"
              src="https://i.pinimg.com/originals/b1/ab/50/b1ab50685a2023c86508830b86389df2.jpg"
            />
            <Card.Body>
              <Card.Title>Radha Patel</Card.Title>
              <Card.Text>
                Radha loves data science. She is our database administrator. She
                also does our data visualization.
              </Card.Text>
            </Card.Body>
            <Card.Footer>
              <small className="text-muted">Last updated 3 mins ago</small>
            </Card.Footer>
          </Card>
          <Card>
            <Card.Img
              variant="top"
              src="https://images.unsplash.com/photo-1509042239860-f550ce710b93?ixlib=rb-1.2.1&w=1000&q=80"
            />
            <Card.Body>
              <Card.Title>Marwa Alqatari</Card.Title>
              <Card.Text>
                Marwa loves software engineering and building programs. She is
                one of our Backend developers.
              </Card.Text>
            </Card.Body>
            <Card.Footer>
              <small className="text-muted">Last updated 3 mins ago</small>
            </Card.Footer>
          </Card>
        </CardDeck>
        <h1 align="middle"> &nbsp;</h1>
        <CardDeck>
          <Card>
            <Card.Img
              variant="top"
              src="https://i.pinimg.com/originals/aa/b6/f2/aab6f2dc557eac416202846a75655342.jpg"
            />
            <Card.Body>
              <Card.Title>Cameron King</Card.Title>
              <Card.Text>
                Cameron loves programming and creating applications. He is one
                of our Frontend developers.
              </Card.Text>
            </Card.Body>
            <Card.Footer>
              <small className="text-muted">Last updated 3 mins ago</small>
            </Card.Footer>
          </Card>
          <Card>
            <Card.Img
              variant="top"
              src="https://i.pinimg.com/originals/1d/97/44/1d9744313f4a33c16385a7a3d031036b.jpg"
            />
            <Card.Body>
              <Card.Title>Samantha Mitchell</Card.Title>
              <Card.Text>
                Samantha loves coding and designing. She is one of our Front end
                developers and a part of our design team.
              </Card.Text>
            </Card.Body>
            <Card.Footer>
              <small className="text-muted">Last updated 3 mins ago</small>
            </Card.Footer>
          </Card>
          <Card>
            <Card.Img
              variant="top"
              src="https://i.pinimg.com/originals/ca/02/4b/ca024b026242b4ae1ebd269580bbb2c3.jpg"
            />
            <Card.Body>
              <Card.Title>Gable Brown</Card.Title>
              <Card.Text>
                Gable loves software systems. He is one of our Backend
                developers and our team's scrum master.
              </Card.Text>
            </Card.Body>
            <Card.Footer>
              <small className="text-muted">Last updated 3 mins ago</small>
            </Card.Footer>
          </Card>
        </CardDeck>
      </div>
    );
  }
}

```

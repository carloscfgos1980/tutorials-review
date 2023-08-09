## Forms examples:
1. The-Net-Ninja_React: input, text area, select option. Separated react values. No bootstrap styling
2. Register in bootstrap tutorial of UI brains. This use the same funtion to grab the value from the form. Unnnesary embed by using (user) but it is useful to check how the deep copy is done.




# 1. The-Net-Ninja_React

# Location in Mac:
/Users/carlosinfante/Desktop/coding-projects/winc-academy/frontend-course/MODULE9 - DEBUGGING and DOMAIN MODELING/REVIEW/react-hooks/useState nd useEffect/The_Net_Ninja-blog-app

# Location in GitHub:
https://github.com/carloscfgos1980/React-useState-useEffect-blog

import { useState } from "react";
import { useHistory } from "react-router-dom";

const Create = () => {
  const [title, setTitle] = useState('');
  const [body, setBody] = useState('');
  const [author, setAuthor] = useState('mario');
  const [isPending, setIsPending] = useState(false);
  const history = useHistory();

  const handleSubmit = (e) => {
    e.preventDefault();
    const blog = { title, body, author };

    setIsPending(true);

    fetch('http://localhost:8000/blogs/', {
      method: 'POST',
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify(blog)
    }).then(() => {
      setIsPending(false);
      // history.go(-1);
      history.push('/');
    })
  }

  return (
    <div className="create">
      <h2>Add a New Blog</h2>
      <form onSubmit={handleSubmit}>
        <label>Blog title:</label>
        <input
          type="text"
          required
          value={title}
          onChange={(e) => setTitle(e.target.value)}
        />
        <label>Blog body:</label>
        <textarea
          required
          value={body}
          onChange={(e) => setBody(e.target.value)}
        ></textarea>
        <label>Blog author:</label>
        <select
          value={author}
          onChange={(e) => setAuthor(e.target.value)}
        >
          <option value="mario">mario</option>
          <option value="yoshi">yoshi</option>
        </select>
        {!isPending && <button>Add Blog</button>}
        {isPending && <button disabled>Adding Blog....</button>}
      </form>
    </div>
  );
}

export default Create;


--------------------------------------------------------------------------------

import { useState } from "react";
import { Button, Card, Col, Container, Form, Row } from "react-bootstrap";

const Register = () => {
    const [state, setState] = useState({
        user: {
            username: '',
            email: '',
            password: ''
        }
    });
    const updateInput = (e) => {
        setState({
            ...state,
            user: {
                ...state.user,
                [e.target.name]: e.target.value
            }
        })
    }
    const register = (e) => {
        e.preventDefault();
        console.log(state.user)
    }
    return (
        <>
            <Container className="mt-3">
                <Row>
                    <Col xs={3}>
                        <Card className="shadow-lg">
                            <Card.Header className="p-3" style={{ backgroundColor: '#ffc107' }}>
                                <h4>Register</h4>
                            </Card.Header>
                            <Card.Body>
                                <Form>
                                    <Form.Group className="mb-3">
                                        <Form.Control
                                            name="username"
                                            onChange={updateInput}
                                            className="mb-3" type='text' placeholder="Username" />
                                        <Form.Control
                                            name="email"
                                            onChange={updateInput}
                                            className="mb-3" type='text' placeholder="Email" />
                                        <Form.Control
                                            name="password"
                                            onChange={updateInput}
                                            className="mb-3" type='text' placeholder="Password" />
                                        <Button
                                            onClick={register}
                                            variant="warning" type="submit">Register</Button>
                                    </Form.Group>
                                </Form>
                            </Card.Body>
                        </Card>

                    </Col>
                </Row>
            </Container>
        </>
    );
}

export default Register;
Responsive React Select with custom user input built with Bootstrap 5. Click on the Other option to input a custom value into the select.

Check out [React Bootstrap Select With Custom Input Documentation](https://mdbootstrap.com/docs/react/extended/select-with-custom-input/) for detailed instructions & even more examples.

## Basic example

![React Bootstrap 5 Select With Custom Input](/assets/basic.png)

```js
import React, { useCallback, useEffect, useMemo, useRef, useState } from "react";
import { MDBContainer, MDBInput, MDBSelect } from "mdb-react-ui-kit";

export default function App() {
  const data = useMemo(
    () => [
      { text: "One", value: 1 },
      { text: "Two", value: 2 },
      { text: "Three", value: 3 },
      { text: "Four", value: 4 },
      { text: "Other", value: 5 },
    ],
    []
  );

  const [currentValue, setCurrentValue] = useState(data[0]);
  const [inputActive, setInputActive] = useState(false);

  const otherInputEl = useRef(null);

  const inputOnBlur = useCallback((e) => {
    if (!e.target.value) {
      setInputActive(false);
      setCurrentValue(data[data.length - 1])
    }
  }, []);

  useEffect(() => {
    console.log(currentValue);
    const lastIndex = data.length - 1;
    if (currentValue.value == data[lastIndex].value) {
      setInputActive(true);
      setTimeout(() => {
        otherInputEl.current?.focus();
      });
    } else {
      setInputActive(false);
    }
  }, [currentValue]);

  return (
    <MDBContainer style={{ width: "300px" }} className="mt-5">
      {inputActive ? (
        <MDBInput onBlur={inputOnBlur} inputRef={otherInputEl} label="Other" id="form1" type="text" />
      ) : (
        <MDBSelect
          onValueChange={(e) => setCurrentValue(e)}
          label="Example label"
          data={data}
        />
      )}
    </MDBContainer>
  );
}
```


## How to use?

1. Download MDB React - free UI KIT

2. Choose your favourite customized component and click on the image

3. Copy & paste the code into your MDB project

[▶️ Subscribe to YouTube channel for web development tutorials & resources](https://www.youtube.com/MDBootstrap?sub_confirmation=1)

___

## More extended Bootstrap documentation

<ul>
<li><a href="https://mdbootstrap.com/docs/react/extended/multiselect/">React multiselect</a></li>
<li><a href="https://mdbootstrap.com/docs/react/forms/select/">React select</a></li>
<li><a href="https://mdbootstrap.com/docs/react/forms/overview/">React forms</a></li>
<li><a href="https://mdbootstrap.com/docs/react/forms/input-fields/">React input fields</a></li>
</ul>

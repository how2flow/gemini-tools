# gemini-tools

## Add gemini tools

### get_tools

Edit bin/get_tools
```
[
  {
    ...
  }, <<< add on new tools with comma
  {
    "name": "foo",
    "description": "A tool that returns the var",
    "parameters": {
      "type": "object",
      "properties": {
        "ret": {
          "type": "...",
          "description": "The var to return."
        }
      },
      "required": ["ret"]
    }
  }
]
```

### set_tools

Edit bin/call_tools
```
...

cmd_foo() {
  local var

  read INPUT_JSON
  var=$(echo "${INPUT_JSON}" | jq -r '.ret')
  echo "{\"result\": \"..."}"
}

...

case ${FUNC_NAME} in
  echo)
    cmd_echo
    ;;
  ...
  foo)
    cmd_foo
    ;;
  *)
    echo "{\"error\": \"Unknown Function: ${FUNC_NAME}\"}"
    ;;
esac

```

## Run gemini

Run gemini include this project<br>
and check with "/tools" gemini inner command<br>

# XML

Encode and decode to and from XML. Whitespace is not conserved for round trips - but the order of the fields are.

As yaml does not have the concept of attributes, xml attributes are converted to regular fields with a prefix to prevent clobbering. This defaults to "+", use the `--xml-attribute-prefix` to change.

Consecutive xml nodes with the same name are assumed to be arrays.

All values in XML are assumed to be strings - but you can use `from_yaml` to parse them into their correct types:


```
yq e -p=xml '.myNumberField |= from_yaml' my.xml
```


XML nodes that have attributes then plain content, e.g:

```xml
<cat name="tiger">meow</cat>
```

The content of the node will be set as a field in the map with the key "+content". Use the `--xml-content-name` flag to change this.

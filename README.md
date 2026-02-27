# VS Code Property List Syntax Highlighting

This is a conversion of the [Property List (XML) TextMate grammar](https://github.com/textmate/property-list.tmbundle) to an injection grammar for XML. It also includes the code snippets from the TextMate bundle.


## Features

- Syntax highlighting for XML Property Lists
- Code snippets for Property List headers and tags
- Compatible with XML extensions
- Compatible with Mike Cunneen's [Property List Editor (updated)](https://marketplace.visualstudio.com/items?itemName=MikeCunneen.cunneen-vscode-plist) and David Nicolson's [Binary Plist](https://marketplace.visualstudio.com/items?itemName=dnicolson.binary-plist)
- Just configuration files, no binaries or scripts.

### Syntax Highlighting
![Before/After](/resources/syntax-highlighting.png)

### Code Snippets
![Code Snippets Preview](/resources/code-snippets.gif)

## Configuration

Add this to your `settings.json`

``` json
{
	"files.associations": {
		"*.plist": "xml",
		"*.mobileconfig": "xml"
	}
}
```

## FAQ

### Why an injection grammar?

This started as a direct conversion of the original TextMate grammar but two problems quickly appeared.

1. VS Code's automatic language detection was determined to mark all Property Lists as XML and nothing I did could prevent it from doing so 100% of the time.

2. Defining a language called `plist` caused conflicts with other extensions for Property Lists that do the same and changing it to something else caused a different set of conflicts.

Pivoting to an injection grammar solved both issues.

### Wait, What is an injection grammar?

A standard TextMate grammar defines a language and is responsible for tokenising every character in a file of that language. A theme then maps colours to those tokens. 

An injection grammar builds upon an existing grammar by injecting additional tokenisation rules into it.


### It doesn't look like the syntax highlighting is working

This is likely due to how your current theme deals with semantic highlighting or maps colours to TextMate scopes. 
You can try setting `"editor.semanticHighlighting.enabled": false` or test with a different theme.

### Does this do formatting?

Nope, but the advantage of it being an injection grammar for XML means you can use your XML formatter of choice. I recommend Red Hat's [XML](https://marketplace.visualstudio.com/items?itemName=redhat.vscode-xml) extension.

---
## Release Notes

### 1.0.0

Initial release

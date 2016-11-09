# luxmail

A template for creating HTML emails.

##Instructions

Party like it's 1999 -- build out the email using nested tables. No javascript and no linked CSS files.

In fact, even CSS in the head is prone to not work in many mail clients. Inline CSS is the only bullet-proof solution.

Mailchimp provides a great tool for converting all CSS to inline:
https://templates.mailchimp.com/resources/inline-css/

##Tips and Tricks

###Nested Tables with Default Fonts
Many versions of outlook break inheritance for font related ruless when tables are nested. Take the following code for example:

```html
<table style="font-family: 'Verdana', 'Arial', sans-serif;">
	<tr>
		<td>
			Text
			<table>
				<tr>
					<td>
						Table 2 Text
					</td>
					<td>
						Table 2 Text
					</td>
				</tr>
			</table>
		</td>
	</tr>
</table>
```
In this example, "Table 2 Text" might default to a font other than the font specified in it's parent table. Solution: Any font related rules need to be re-applied when nesting tables, like so:

```html
<table style="font-family: 'Verdana', 'Arial', sans-serif;">
	<tr>
		<td>
			Text
			<table style="font-family: 'Verdana', 'Arial', sans-serif;">
				<tr>
					<td>
						Table 2 Text
					</td>
					<td>
						Table 2 Text
					</td>
				</tr>
			</table>
		</td>
	</tr>
</table>
```
### Images with Space Underneath

Sometimes, an image may appear with a small, unwanted space beneath them. This space will go away if the image is set to `display: block`.

```html
<img src="example.jpg" alt="An example" style="display:block;" />
```

### Gigantic Images in Mobile Gmail

On mobile Gmail, sometimes images will appear to grow in size while the text and other elements in the same table will not. This seems like some attempt by Gmail to try and force the email to look more "responsive", but often times harms the design and it's legibility. Adding a `width` AND a `min-width` to the containing table seems to fix.

```html
<table style="width:600px; min-width:600px;">
	<tr>
		<td>
			<img src="example.jpg" alt="An example" style="display:block;" />
		</td>
		<td>
			<p>Example paragraph text.</p>
		</td>
	</tr>
</table>
````

Insert Paragraph Tags

Some versions of outlook will wrap text in a `<p>` tag if it is not wrapped in a block level text element, such as `<p>`, `<h1>`, `<li`>. This happens even inside of `<td>`. These `<p>` tags might display with a margin, which can cause unexpected spaces in the design.

How the code is written:

```html
Lorem ipsum dolor sit amet, consectetur adipiscing elit.
```

What Outlook does to the code:
```html
<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
```

It is wise to make sure that all text is wrapped in a `<p>` or other block level text element, that way you know how it's going to look before it hits Outlook.

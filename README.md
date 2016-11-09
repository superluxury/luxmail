# luxmail

A template for creating HTML emails.

##Instructions

Party like it's 1999 -- build out the email using nested tables. No javascript and no linked CSS files.

In fact, even CSS in the head is prone to not work in many mail clients. Inline CSS is the only bullet-proof solution.

Mailchimp provides a great tool for convertin all CSS to inline:
https://templates.mailchimp.com/resources/inline-css/

##Tips and Tricks

###Nested Tables with Default Fonts
Many versions of outlook break inheritance for font relrted ruless when tables are nested. Take the following code for example:

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

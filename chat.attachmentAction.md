# chat.attachmentAction
This method interacts with the attachments in interactive messages (buttons, menus, etc.)

## Arguments
This method has the URL `https://slack.com/api/chat.attachmentAction` and follows the [Slack Web API calling conventions](https://api.slack.com/web#basics).

Argument|Example|Required|Description
--------|-------|--------|-----------
`token`|`xxxx-xxxxxxxxx-xxxx`|Required|Authentication token (Requires scope: `post`)
`channel_id`|`C12345678`|Required|The channel ID containing the original message (located in message["channel"])
`actions`|`[{"id":"1","name”:”Acknowledge","text”:”Acknowledge","type":"button","value”:”Acknowledge","style":"primary"}]`|Required|An array containing the action(s) that are being used `(located in message["attachments"][attachment_num]["actions"][choice_num])`
`attachment_id`|`1`|Required|The ID of the attachment being acted on `(located in message["attachments"][0]["id"])`
`callback_id`|`xxxxxxxxx`|Required|The callback ID of the original message `(located in message["attachments"][0]["callback_id"])`
`message_ts`|`1510863690`|Required|The timestamp of the original message `located in message["ts"]`
`service_id`|`BXXXXXXXX`|Optional\*|The bot ID of the original message `(located in message["bot_id"])`
`bot_user_id`|`WXXXXXXXX` |Optional\*|The user ID of the original message  `(located in message["user])`

\* - At least one of these is required, i.e. you must include one, the other, or both.


## Response
You will receive a response in JSON indicating if the command has been executed successfully or not with the `ok` variable and whether the original message has been replaced with an update version or not.

```json
{
"replaced":true,
"ok":true
}
```
In case of errors you will receive a standard Slack API response in JSON as described [here](https://api.slack.com/web#basics).

## Errors & Warnings
Error|Description
--------|-------
`missing_scope`|The method requires the scope `post`. Since this scope does not seam to be availble in the app config window you need to provide a legacy token for this to work.

tbd

# Incoming Message
## Structure
Incoming Message it is object(SSilence\ImapClient\IncomingMessage) has 5 basic properties
```
$imap->incomingMessage->header
$imap->incomingMessage->message
$imap->incomingMessage->attachment
$imap->incomingMessage->section
$imap->incomingMessage->structure
```
and one for debugging
```
$imap->incomingMessage->debug
```
### Header propertie
Header propertie looks like
```
["header"]=>
  object(stdClass)#3 (15) {
    ["subject"]=>
    string(10) "..."
    ["from"]=>
    string(36) "..."
    ["to"]=>
    string(36) "..."
    ["date"]=>
    string(31) "Tue, 21 Mar 2017 11:02:37 +0000"
    ["message_id"]=>
    string(37) "<1490094157.905281607@f369.i.gmail.com>"
    ["size"]=>
    int(472418)
    ["uid"]=>
    int(42243)
    ["msgno"]=>
    int(82)
    ["recent"]=>
    int(0)
    ["flagged"]=>
    int(0)
    ["answered"]=>
    int(0)
    ["deleted"]=>
    int(0)
    ["seen"]=>
    int(1)
    ["draft"]=>
    int(0)
    ["udate"]=>
    int(1490094157)
  }
```
To get the subject of the message, use
$imap->incomingMessage->header->subject

### Message propertie
Message propertie looks like
```
["message"]=>
  object(stdClass)#29 (3) {
    ["plain"]=>
    string(16) "text message"
    ["info"]=>
    array(2) {
      [0]=>
      object(stdClass)#27 (2) {
        ["structure"]=>
        object(stdClass)#28 (11) {
          ["type"]=>
          int(0)
          ["encoding"]=>
          int(3)
          ["ifsubtype"]=>
          int(1)
          ["subtype"]=>
          string(5) "PLAIN"
          ["ifdescription"]=>
          int(0)
          ["ifid"]=>
          int(0)
          ["bytes"]=>
          int(20)
          ["ifdisposition"]=>
          int(0)
          ["ifdparameters"]=>
          int(0)
          ["ifparameters"]=>
          int(1)
          ["parameters"]=>
          array(1) {
            [0]=>
            object(stdClass)#33 (2) {
              ["attribute"]=>
              string(7) "charset"
              ["value"]=>
              string(5) "utf-8"
            }
          }
        }
        ["body"]=>
        string(16) "text message"
      }
      [1]=>
      object(stdClass)#30 (2) {
        ["structure"]=>
        object(stdClass)#31 (11) {
          ["type"]=>
          int(0)
          ["encoding"]=>
          int(3)
          ["ifsubtype"]=>
          int(1)
          ["subtype"]=>
          string(4) "HTML"
          ["ifdescription"]=>
          int(0)
          ["ifid"]=>
          int(0)
          ["bytes"]=>
          int(72)
          ["ifdisposition"]=>
          int(0)
          ["ifdparameters"]=>
          int(0)
          ["ifparameters"]=>
          int(1)
          ["parameters"]=>
          array(1) {
            [0]=>
            object(stdClass)#34 (2) {
              ["attribute"]=>
              string(7) "charset"
              ["value"]=>
              string(5) "utf-8"
            }
          }
        }
        ["body"]=>
        string(56) "<HTML><BODY><br><br><br>html text message<br></BODY></HTML>"
      }
    }
    ["html"]=>
    string(56) "<HTML><BODY><br><br><br>html text message<br></BODY></HTML>"
  }
```
$imap->incomingMessage->message->info it is array. He is always.
$imap->incomingMessage->message->html
and
$imap->incomingMessage->message->plain
Generated automatically from the message structure.
If there is subtype=HTML then it will.

To get the body of the message, use
$imap->incomingMessage->message->html
or
$imap->incomingMessage->message->plain

### Attachment propertie
Attachment propertie it is array objects.
If the letter has attachments, then
```
["attachment"]=>
  array(2) {
    [0]=>
    object(stdClass)#18 (2) {
      ["structure"]=>
      object(stdClass)#19 (13) {
        ["type"]=>
        int(5)
        ["encoding"]=>
        int(3)
        ["ifsubtype"]=>
        int(1)
        ["subtype"]=>
        string(4) "JPEG"
        ["ifdescription"]=>
        int(0)
        ["ifid"]=>
        int(0)
        ["bytes"]=>
        int(237916)
        ["ifdisposition"]=>
        int(1)
        ["disposition"]=>
        string(10) "attachment"
        ["ifdparameters"]=>
        int(1)
        ["dparameters"]=>
        array(1) {
          [0]=>
          object(stdClass)#25 (2) {
            ["attribute"]=>
            string(8) "filename"
            ["value"]=>
            string(12) "Location.jpg"
          }
        }
        ["ifparameters"]=>
        int(1)
        ["parameters"]=>
        array(1) {
          [0]=>
          object(stdClass)#24 (2) {
            ["attribute"]=>
            string(4) "name"
            ["value"]=>
            string(12) "Location.jpg"
          }
        }
      }
      ["body"]=>string(173862) ""
      
      ... and next object ...
      [1]=>
          object(stdClass)#18 (2) {}
          
```
Attachment object has 2 basic properties.
$imap->incomingMessage->attachment[0]->structure
and
$imap->incomingMessage->attachment[0]->body
Body propertie contains an attachment.

### Section propertie
Section propertie it is array sections of which the letter consists.
```
["section"]=>
  array(5) {
    [0]=>
    string(1) "1"
    [1]=>
    string(1) "2"
    [2]=>
    string(1) "3"
    [5]=>
    string(3) "1.1"
    [7]=>
    string(3) "1.2"
  }
```
### Structure propertie
Structure propertie it is a complete structure of the letter
### Debug propertie
Debug propertie it is propertie for debuging.
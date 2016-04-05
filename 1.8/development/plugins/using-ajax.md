---
layout: page
title:  "Using AJAX"
categories: [plugins]
---

## Serving AJAX requests

If you need to respond to AJAX requests you can use the `xmlhttp` hook:

```php
// With your other hooks
$plugins->add_hook('xmlhttp', 'ajax_action');

// In the body of your plugin
function ajax_action()
{
    global $mybb, $charset;

    if($mybb->get_input('action') == 'my_ajax')
    {
        header("Content-type: application/json; charset={$charset}");
        $data = array('hello' => 'world');
        echo json_encode($data);
        exit;
    }
}
```

This will output a JSON encoded response of the `$data` array when accessing `xmlhttp.php?action=my_ajax`.

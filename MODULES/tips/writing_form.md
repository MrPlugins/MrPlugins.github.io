In *__inCipit__* writing a form is very simple too.
There are many callback and mode action that you can set via `data-*` attributes.

Below is an example of a form:

```php
<?php
$isEdit = isset($uniqid) ? TRUE : FALSE; // to understand if we are into a creation or update part
<div class="row">
  <div class="col-md-12">
        <div class="hidden messagesContainer"></div>
            <form id="products_form"
            data-after-complete-msg-hook-function="close_modal_products_form"
            method="post"
            action="<?= url_base($this->router->module . '/' . $this->router->class . '/' . ($isEdit ? 'update' : 'create')); ?>"
            role="form"
            data-action="<?= $isEdit ? 'update' : 'create'; ?>"
            class="with-validation ajaxForm">
                ... YOUR INPUTS HERE ...

                <button type="submit" class="hidden"><?php echo lang('syslang_save_button_label'); ?></button>
            </form>
        </div>
    </div>
</div>
```

```code
    <div class="hidden messagesContainer"></div>
    this div will be container for errors and/or warnings messages (for validation)
    you can change this container via data-message-container="YOUR_CONTAINER_SELECTOR_ID_OR_CLASS"

```


```code
    class="with-validation ajaxForm"

    - with-validation will active the jquery validate plugin for all input form, you can declare ignore class on you input to skip validation
    - ajaxForm will send form via ajax for a user friendly experience
```


### Possible `data-*` attributes:

These data tags will define a custom function to use in js:

<code>data-before-submit-hook-function -></code> fires before submit form\
<code>data-before-serialize-load-hook-function</code> -> fires before serialization of form data\
<code>data-after-serialize-load-hook-function</code> -> fires after serialization of form data\
<code>data-before-complete-load-hook-function</code> -> fires before the message of `complete` method of ajax call\
<code>data-before-complete-msg-hook-function</code> -> fires before the loader disappare into `complete` method of ajax call\
<code>data-after-complete-msg-hook-function</code> -> fires after the message `complete` method of ajax call\
<code>data-before-success-hook-function]</code> -> fires before the message into `success` method of ajax call

<code>data-type</code> define the ajax dataType; possible value : `JSON` (default), `HTML` or `JSONP`\
<code>data-msg-format</code> possible value: `swal` (default) for return message with [SweetAlert plugin]('https://sweetalert2.github.io ':target=_blank') or `slide` to show message into the slide div\
<code>data-with-confirmation</code> allow to show a confirmation dialog with custom html before send form with the final choice


>[!INFO]
> This attributes are useful to set into your js file some callback functions in different moments (like hocks)\
> you can access to <code>$this</code> object that will be refer to form

## Writing inputs

There are a shortcode system to write inputs into a form with bootstrap rules\
e.g:

```code
    <input data-label="E-mail"
        data-col="md-9,lg-12"
        data-help-block="Help block" -> you can specify a selector too, eg. #elementContainingHelpText, it will be detach from dom taking its text for helblock
        data-addon="<i class='fa fa-...\'></i>"
        data-addon-right
        data-label-col="md-9,lg-12"
        type="text"
        name="email"
        id="email"
        value=""
        class="form-control required email" />
```
it will be :

```code
    <div class="form-group col-md-9 col-lg-12">
    	<label class="control-label" for="email">E-mail</label>
    	<input type="text" name="email" id="email" class="form-control required email" value="" aria-required="true">
        <span class="help-block">Help block</span>
    </div>

```

All `data-*` attributes are optional, you can write your inputs manually without using shortcode
>[!TIP]
>to not automatically wrap a field use the class "no-wrap"
> p.s. data-label-col is helpful for forms with form-horizontal class, not use it for regular forms
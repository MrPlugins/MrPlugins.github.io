*__inCIpit__* integrates a third-party but customized [Responsive filemanager 9](https://www.responsivefilemanager.com/ ':target=_blank')\

### Integrate upload via filemanager

The html

```html
<div class="fm-container" data-fldr="products" data-type="1" data-default-img="<?= asset_url('img/default-img.jpg'); ?>" data-preview-size="300">
    <input type="hidden" class="fm-input" name="main_img" id="main_img" value="" />
    <img src="<?= asset_url('img/default-img.jpg') ?>" class="fm-thumbs img-responsive center-block" />
    <br/>
    <a class="btn btn-default btn-fm btn-block flat"><i class="fa fa-upload"></i> <?= lang('label_add_main_img'); ?></a>
    <span class="btn btn-danger btn-block flat btn-fm-delete"><i class="fa fa-trash"></i>  <?= lang('syslang_cancel_button_label'); ?></span>
</div>
```

## data-* attributes
<code>data-fldr</code>: name of directory where stored files, if not exists the system will create it\
<code>data-type</code>: define the file type to show for upload - 1:images files 2:all files 3:video files\
<code>data-sort-by</code>: the element to sorting (values: name,size,extension,date)\
<code>data-descending</code>: descending or ascending (values=1 or 0) default="0"\
<code>data-lang</code>: the language code e.g. (EN,IT…) default=current admin language"\
<code>data-relative-url</code>: should be added to the request with a value of "1" when opening FILE MANAGER. Otherwise returned URL-s will be absolute default="1"\
<code>data-default-img</code>: the default image before loaded from filemanager\
<code>data-preview-size</code>: 70,50,300,600,"" (if "" keep the original image)\
<code>data-thumb-class</code>: adding class to image thumbnail\
<code>Data-multi</code> allow to select multiple file into filemanager


the result:

<img src="./assets/img/filemanager.png" style="width:300px;">
<img src="./assets/img/filemanager2.png" style="width:300px;">
<img src="./assets/img/filemanager3.png" style="width:300px;">


<br>
<br>

> [!NOTE]
> Into products module there is an example for single and multiple files upload via FILE MANAGER
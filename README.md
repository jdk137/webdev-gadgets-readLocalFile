# webdev-gadgets-readLocalFile
read local file's text content through html5 file api

[demo](https://rawgit.com/jdk137/webdev-gadgets-readLocalFile/master/index.html)

``` html

<!DOCTYPE html>
<html lang="en">
<head>
  <title>html5 file api.js</title>
  <meta charset="utf-8" />
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
  <style>

  input.upload {
    display: none;
  }

  textarea {
    width: 300px;
    height: 200px;
  }

  </style>
</head>
<body>
  <button class="upload">upload</button>
  <input type="file" class="upload"/><br>
  <textarea></textarea>
</body>
<script>
      // click button to trigger file upload
      $('button.upload').on('click', function () {
        $('input.upload').focus().trigger('click');
      });
      $('body').on('change', 'input.upload', function(event) {
        var input = event.target;
        var reader = new FileReader();
        reader.onload = function(){
          var text = reader.result;
          var $editor = $('textarea');
          $editor.val($editor.val() + ';' + text);
        };

        // prevent always upload the first file.
        var $input = $('input.upload');
        $input.replaceWith($input.clone(true));

        reader.readAsText(input.files[0]);
      });

</script>
</html>
```
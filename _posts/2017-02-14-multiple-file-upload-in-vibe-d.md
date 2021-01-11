---
title: "Multiple file upload in vibe.d"
date: 2017-02-14 16:00:00
categories: [programming]
tags: [d, vibe.d, web development]
---

![Multiple files upload form](/images/multiple-file-upload-form.png)

Previously, I did a demo on
[how to submit a form in vibe.d](https://aberba.com/2016/form-upload-in-vibe-d/)
including a file upload. Now its time to demo multiple file upload which
sometimes come in handy. This post serves as continuation so refer to it to
catch up.

Similar to the previous post, we will create an `upload` function which will
handle file uploads on the server side. However, I will only implement the
multiple file upload functionality without boring you with textual data which I
did [previously](https://aberba.com/2016/form-upload-in-vibe-d/). Create a new
vibe.d project and build upon it to a point where you have the `upload` function
(You may use code from the previous post).

So lets rock and roll ASAP, shall we. Multiple file input (of any number) can be
specified in an HTML form by appending square brackets (`"[]"`) to the value of
the `name` property.

> Using JavaScript, you can dynamically add file inputs to allow user to upload
> several file at a time.

The diet template code will be:

```jade
doctype html
head
    title File upload
body
    form(method='post',action='/upload',enctype='multipart/form-data')
        p
            label(for='picture[]') Select multiple pictures
            br
            input(name='picture[]', type='file')
            br
            input(name='picture[]', type='file')

        button(type='submit') Upload
```

The `enctype='multipart/form-data'` is necessary to submit files in a form as
discussed in my previous post. As you can see, the value of the `name` property
of all the file inputs is `picture[]`. This makes it easy to identify all those
files, as we will see below, as belonging to the same category. This is
particularly useful for uploading one or more of a certain file without having
to give each file a unique `name` value for identification on the server side.

Within the `upload` function, add the following code:

```d
void upload(HTTPServerRequest req, HTTPServerResponse res)
{
    import std.conv: to;
    import std.path: extension;

    foreach(nameAttr, picture; req.files) {

        // Extract file extension
        string ext = extension(to!string(picture.filename));

        // Sort files based on "name" attribute
        // Only files with name="picture[]" will be uploaded
        if (nameAttr == "picture[]" && (ext == ".png" || ext == ".jpg"))
        {
            import std.datetime: Clock;
            // Rename uploaded file using current timestamp to make it unique
            string newFileName = "image_" ~ to!string(Clock.currTime.toUnixTime) ~ ext;

            try {
                logInfo("Move successful!");
                moveFile(picture.tempPath, Path("./public/pictures/" ~ newFileName));
            } catch (Exception e) {
                logInfo("Exception thrown");
                copyFile(picture.tempPath, Path("./public/pictures/" ~ newFileName));
            }
        }
    }

    res.redirect("/");
}
```

The extension of each uploaded file is extracted using the `extension` function
from `std.path` to be used in renaming. We then iterate over the submitted files
in the form to filter out those that do not have a `name` value of `picture[]`.
As common in file uploads, you may also choose to only allow files of certain
extension (".png", ".jpg", ".jpeg", ".gif,", ".pdf", etc), which I implemented
only for image files with either ".png" or ".jpg" extension.

Uploaded files may contain certain characters which are not allowed in some
Operating Systems, and one approach is by giving each file a custom file name
which you can guarantee will not cause any issues. I therefore renamed each file
as `"image_"` appended with the current
[Unix timestamp](https://en.wikipedia.org/wiki/Unix_time) and the file
extension. The file is then moved to `public/pictures/` or copied in-case an
exception is thrown (who knows what else can happen).

> Make sure you create the `pictures` directory in your `public` folder.

That's all it takes to upload multiple files in vibe.d, I may demo how to
implement the same functionality using the `Web Interface` of vibe.d but not
until I write an introductory blog about it and why you _really_ need to use it
in most cases.

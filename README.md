# WordPress-Media-Modal-Image/File-Uploads

This is a sample to show how you can open the admin media modal and how to get a single or multiple images/files selected via the WordPress admin media modal.
Tested with WordPress Version 6.0 <br/>
<b>SCREENSHOTS AVAILABLE AT THE BOTTOM OF THE WEB PAGE</b>

# Enqueue your javascript file and all media JS APIs.

Enqueue your javascript file and all media JS APIs. 

        add_action('admin_enqueue_scripts', function() {
            wp_enqueue_media(); // Enqueues all scripts, styles, settings, and templates necessary to use all media JS APIs.
            wp_enqueue_style("sample.js", "your-path/sample.js", array(), "1.0.0", false);
        });
        
# HTML SAMPLE

(a) href="#" id="open_modal_link">Open Modal (/a)

# How to open the Media Frame & Get Info for a single image/file

        // Select open modal link
        let open_modal_link = document.getElementById("open_modal_link");
        
        open_modal_link.addEventListener("click", function(e) {
                e.preventDefault();
                // Creates a new media frame
                let frame = wp.media({
                    title: "Add Your Own Title Here",
                    button: {
                        text: 'Add Your Own Text Here'
                    },
                    multiple: false
                });
                frame.open();

                // When an image is selected in the media frame...
                frame.on('select', function() {

                    // Get media attachment details from the frame state
                    let attachment = frame.state().get('selection').first().toJSON();
                    // Log the attachment object for more info
                    console.dir(attachment);
                    // Get the Image URL from the attachment object
                    let image_url = attachment.url;
                });
        });
        
# How to open the Media Frame & Get Info for a Multiple Images/Files

        // Select open modal link
        let open_modal_link = document.getElementById("open_modal_link");

        open_modal_link.addEventListener("click", function(e) {
                e.preventDefault();
                // Creates a new media frame
                let frame = wp.media({
                    title: "Add Your Own Title Here",
                    button: {
                        text: 'Add Your Own Text Here'
                    },
                    multiple: true
                });
                frame.open();

                // When multiple images are selected in the media frame...
                frame.on('select', function() {

                    // Get media attachment details from the frame state
                    let attachment = frame.state().get('selection').toJSON();
                    // Log the Array
                    console.dir(attachment);
                });
        });

# SCREENSHOTS

![test1](https://user-images.githubusercontent.com/79761312/178506838-2e4cff20-f992-4553-8086-4686f7c4f15a.PNG)
![test2](https://user-images.githubusercontent.com/79761312/178506874-4c9d711e-dde0-4849-baeb-3bd585f8b3fa.PNG)
![test3](https://user-images.githubusercontent.com/79761312/178506901-c8e23456-b3bc-4230-95fa-0880ef89fa83.PNG)
![test4](https://user-images.githubusercontent.com/79761312/178506945-510be71a-0474-46ee-aa24-448c6163d070.PNG)
![test5](https://user-images.githubusercontent.com/79761312/178507016-858b81f7-8f0a-4129-94ac-017412c077a7.PNG)
![test6](https://user-images.githubusercontent.com/79761312/178507040-65318d60-d703-47a0-8a23-d925a3943105.PNG)





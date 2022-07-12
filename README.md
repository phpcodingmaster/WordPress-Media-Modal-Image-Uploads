# WordPress-Media-Modal-Image-Uploads

This is a sample to show how you can open the admin media modal and how to get a single or multiple images selected via the WordPress admin media modal.
Tested with WordPress Version 6.0 <br/>

# Enqueue your javascript file and all media JS APIs.

Enqueue your javascript file and all media JS APIs. 

        add_action('admin_enqueue_scripts', function() {
            wp_enqueue_media(); // Enqueues all scripts, styles, settings, and templates necessary to use all media JS APIs.
            wp_enqueue_style("sample.js", "your-path/sample.js", array(), "1.0.0", false);
        });
        
# HTML SAMPLE

(a) href="#" id="open_modal_link">Open Modal (/a)

# How to open the Media Frame & Get Info for a single image

        // Select open modal link
        let open_modal_link = document.getElementById("open_modal_link");

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
        
# How to open the Media Frame & Get Info for a Multiple Images

        // Select open modal link
        let open_modal_link = document.getElementById("open_modal_link");

        // Creates a new media frame
        let frame = wp.media({
            title: "Add Your Own Title Here",
            button: {
                text: 'Add Your Own Text Here'
            },
            multiple: true
        });
        frame.open();

        // When an image is selected in the media frame...
        frame.on('select', function() {

            // Get media attachment details from the frame state
            let attachments = frame.state().get('selection').toJSON();
            // Log the array of images selected to the console
            console.dir(attachments);
        });

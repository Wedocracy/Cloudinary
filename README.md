Cloudinary Component for CakePHP 2.x
====================================
A Cakephp component for Cloudinary cloud image service.

# Installation
1. Download and extract Cloudinary PHP library from https://github.com/cloudinary/cloudinary_php to app/Vendor/Cloudinary

2. Download from https://github.com/Wedocracy/cakephp-cloudinary

3. Set variables in app/Config/bootstrap.php

			// Cloudinary.env - sign up and get this from http://cloudinary.com
			// Cloudinary.path - tmp path for images
			Configure::write(
				'Cloudinary', 
				array(
					'env' =>  '',
					'path' => APP . 'webroot' . DS . 'img' . DS . 'photos'
				)
			);

4. Place CloudinaryComponent.php in app/Controller/Component/

5. Done!

# Usage

Call the component in controller

			class ExampleController extends AppController {
				public $name = 'Example';

				public $components = array(
					'CloudinaryComponent'
				);

				public function index() {
					// Assume you have already uploaded images to tmp locations
					$this->Cloudinary->upload($file);
				}
			}	

# new tag: cl_images_by_tag($tag) 

*extended by/for wedocracy*

Looks for all images with a given tag.

	$peaches = $this->Cloudinary->cl_images_by_tag('peaches');
	
will give you an array of image data for cloudinary tag "peaches". Then you can do stuff in your view, in conjunction with the other cloudinary methods.

	$peaches = $this->Cloudinary->cl_images_by_tag('peaches');
	foreach ($peaches as $peach):
		echo '<div>';
			echo cl_image_tag($peach['url'], array("crop" => "fill",'width' => 96,'height' => 96,'alt' => 'photo of a peach'),'title' => h('peaches are both fuzzy and tasty'),'class' => 'img-thumbnail'));
		echo '</div>';
	endforeach;

	
# Limitation
	Currently, it only supports uploading and deleteing images. 

# Need help or want to contribute?
	Please feel free to drop me a note.
	
	
## php-cloudfront-invalidate

A Lightweight PHP class for making AWS CloudFront Invalidation requests.

Heavily inspired by: https://github.com/subchild/CloudFront-PHP-Invalidator but I wanted something pure PHP that didn't require additional modules or for the full AWS SDK and all its requirements to be installed.  Also I wanted something that was CodeIgniter friendly.

### Example standalone usage:
1. Include/require the class
```
require 'Cloudfront_invalidator.php';
```
2. Instantiate an object passing credentials and cloudfront distribution id
```
$invalidator = new Cloudfront_invalidator('AWS ACCESS KEY', 'AWS SECRET', 'CLOUDFRONT DIST ID');
```
3. Make an invalidation
```
try {
    $invalidator->invalidate('/images/*');
} catch(Exception $e) {
    echo $e->getMessage() . "\n";
}
```

### Example CodeIgniter Usage
1. Download the file into your application/libraries directory
2. Load the library where desired
```
$this->load->library('cloudfront_invalidator');
```
3. Set your AWS credentials and cloudfront distribution id.  Note, this could be passed to the load library call into constructor.
```
$this->cloudfront_invalidator->setAwsInfo($aws_key, $aws_secret, $aws_dist_id);
```
Make an invalidation
```
try {
    $invalidator->invalidate('/images/*');
} catch(Exception $e) {
    echo $e->getMessage() . "\n";
}
```

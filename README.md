# Justin Zimmerman's Personal Blog

Dear future Justin,

If you've found yourself here, you're probably being ambitious and updating your blog again.

Please find the steps to build and deploy that you've probably forgotten about by now:

  * `brew update && brew upgrade` to get the latest version of Hugo
  * Run `hugo` to build
  * Test things out locally with `hugo server`
  * S3 Upload with Cache Control `aws s3 sync . s3://justinzimmerman.net --force --cache-control max-age=86400`
  * (optional) create a cache invalidation on Cloudfront
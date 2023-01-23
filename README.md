# Laravel PDFMerger

## Install

Via Composer

``` bash
$ composer require serhiikamolov/laravel-pdfmerger
```

## Setup

Add the service provider to the providers array in `config/app.php`.

``` php
'providers' => [
    ...
    PDFMerger\Providers\PDFMergerServiceProvider::class
],

'aliases' => [
    ...
    'PDFMerger' => PDFMerger\Facades\PDFMergerFacade::class
]
```

## Usage
A basic usage example:

``` php
use PDFMerger\Facades\PDFMergerFacade as PDFMerger;

$oMerger = PDFMerger::init();

$oMerger->addPDF('/path/to/project/vendors/webklex/laravel-pdfmerger/src/PDFMerger/examples/pdf_one.pdf', [2]);
$oMerger->addPDF('/path/to/project/vendors/webklex/laravel-pdfmerger/src/PDFMerger/examples/pdf_two.pdf', 'all');

$oMerger->merge();
$oMerger->save('merged_result.pdf');

```

...add raw content data:

``` php
$oMerger->addString(file_get_contents('/path/to/project/vendors/webklex/laravel-pdfmerger/src/PDFMerger/examples/pdf_two.pdf'), [1]);

```

...select the pages you want to merge:

``` php
$oMerger->addPDF($file, 'all');  //Add all pages
$oMerger->addPDF($file, [1]);    //Add page one only
$oMerger->addPDF($file, [2]);    //Add page two only
$oMerger->addPDF($file, [1, 3]); //Add page one and three only

```

...merge files together but add blank pages to support duplex printing:
```php
$oMerger->duplexMerge();
```

...stream the merged content:

``` php
$oMerger->stream();

```
...download the merged content:

``` php
$oMerger->download();

```
..get the raw content data:
``` php
echo $oMerger->output();

```
...set the filename if you don't want to do it later:

``` php
$oMerger->setFileName('example.pdf');

```
## Credits

- [Webklex][link-author]
- All Contributors

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
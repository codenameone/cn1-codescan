# Codename One CodeScanner Library

This library provides code scanning (QR code and Bar code) support for Codename One.  This comprises a refactoring of the `com.codename1.codescan` package into a separate cn1lib so that only applications that require this feature need include it.  The codescan package in the core Codename One library will be deprecated in the future, and this library will be the officially supported method of code scanning in Codename One.


## License

Apache 2.0

## Features

* Scan QR Codes with device camera
* Scan Bar Codes with device camera

## Supported Platforms

Use `CodeScanner.isSupported()` to find out if it is supported on the current platform.

* iOS - Supported and tested
* Android - Supported and tested
* Simulator - Not supported yet
* Javascript - Not supported yet
* RIM - Implemented but not tested
* WinPhone - Not supported yet
* J2ME - Implemented but not tested

## Installation

Copy [cn1-codescan.cn1lib](https://github.com/codenameone/cn1-codescan/raw/master/cn1-codescan.cn1lib) into your project's "lib" directory and refresh libs.

## Usage Example

Scanning QR Code:

~~~~
...
import com.codename1.ext.codescan.CodeScanner;
import com.codename1.ext.codescan.ScanResult;
...

    CodeScanner.getInstance().scanQRCode(new ScanResult() {

        public void scanCompleted(String contents, String formatName, byte[] rawBytes) {
            //barCode.setText("Bar: " + contents);
            cnt.addComponent(new Label(contents));
            cnt.revalidate();
        }

        public void scanCanceled() {
            System.out.println("cancelled");
        }

        public void scanError(int errorCode, String message) {
            System.out.println("err " + message);
        }
    });
~~~~

Scanning Bar Code:

~~~~
...
import com.codename1.ext.codescan.CodeScanner;
import com.codename1.ext.codescan.ScanResult;
...

    CodeScanner.getInstance().scanBarCode(new ScanResult() {

        public void scanCompleted(String contents, String formatName, byte[] rawBytes) {
            //barCode.setText("Bar: " + contents);
            cnt.addComponent(new Label(contents));
            cnt.revalidate();
        }

        public void scanCanceled() {
            System.out.println("cancelled");
        }

        public void scanError(int errorCode, String message) {
            System.out.println("err " + message);
        }
    });   
~~~~

## Documentation

* [Javadocs](http://shannah.github.io/cn1-codescan/javadoc/index.html)

## Building From Source

~~~~
$ git clone https://github.com/codenameone/cn1-codescan.git
$ cd cn1-codescan
$ ant -f configure.xml
$ ant jar
~~~~

You'll find `cn1-codescan.cn1lib` inside the `dist` directory.

NOTE:  The `ant -f configure.xml` is only necessary the first time you build the source.  It will download some dependencies
like JavaSE.jar, CodenameOne.jar, etc.. that were not included with this repository to save space.

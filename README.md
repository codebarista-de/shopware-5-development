# Shopware 5

Fork of the official https://github.com/shopware5/shopware repository.
Uses docker compose, phpenv (optional) and symfony-cli to run a shopware 5 dev instance.

### Requirements

- PHP 8.2.29
- [Symfony CLI](https://symfony.com/download)
- Docker and docker compose

#### Required PHP extensions:

-   <a href="https://php.net/manual/en/book.ctype.php" target="_blank">ctype</a>
-   <a href="https://php.net/manual/en/book.curl.php" target="_blank">curl</a>
-   <a href="https://php.net/manual/en/book.dom.php" target="_blank">dom</a>
-   <a href="https://php.net/manual/en/book.filter.php" target="_blank">filter</a>
-   <a href="https://php.net/manual/en/book.hash.php" target="_blank">hash</a>
-   <a href="https://php.net/manual/en/book.iconv.php" target="_blank">iconv</a>
-   <a href="https://php.net/manual/en/book.image.php" target="_blank">gd</a> (with freetype and libjpeg)
-   <a href="https://php.net/manual/en/book.json.php" target="_blank">json</a>
-   <a href="https://php.net/manual/en/book.mbstring.php" target="_blank">mbstring</a>
-   <a href="https://php.net/manual/en/book.openssl.php" target="_blank">OpenSSL</a>
-   <a href="https://php.net/manual/en/book.session.php" target="_blank">session</a>
-   <a href="https://php.net/manual/en/book.simplexml.php" target="_blank">SimpleXML</a>
-   <a href="https://php.net/manual/en/book.xml.php" target="_blank">xml</a>
-   <a href="https://php.net/manual/en/book.zip.php" target="_blank">zip</a>
-   <a href="https://php.net/manual/en/book.zlib.php" target="_blank">zlib</a>
-   <a href="https://php.net/manual/en/ref.pdo-mysql.php" target="_blank">PDO/MySQL</a>
-   <a href="https://php.net/manual/de/book.fileinfo.php" target="_blank">fileinfo</a>

#### Installing PHP with phpenv

1. Install https://github.com/phpenv/phpenv with https://github.com/php-build/php-build into `~/.phpenv` (as recommended)
2. Add `~/.phpenv/bin` to `PATH`
3. Execute `~/.phpenv/plugins/php-build/install-dependencies.sh`
4. Install PHP 8.2.29: `phpenv install 8.2.29`

### Installation

1.) Clone the git repository to the desired location using:

    git clone https://github.com/codebarista-de/shopware-5-development.git

In case you wish to contribute to Shopware, fork the `5.7` branch rather than cloning it, and create a pull request via GitHub.
For further information please read the section ["Get involved"](#get-involved) of this document.

2.) Set the correct directory permissions:

    chmod -R 755 custom/plugins
    chmod -R 755 engine/Shopware/Plugins/Community
    chmod -R 755 files
    chmod -R 755 media
    chmod -R 755 var
    chmod -R 755 web

Depending on your server configuration, it might be necessary to set whole write permissions (777) to the files and folders above.
You can also start testing with lower permissions due to security reasons (644 for example) as long as your PHP process can write to those files.

3.) A [Makefile](https://www.gnu.org/software/make/manual/make.html) may be used to set up the configuration and database connection:

* ``make init``

**Info regarding platform inter-compatibility**

The `Makefile` is intended to work with Linux and Mac systems alike which means that we're not able to use all features of modern GNU make.
Some workarounds are in place because of this and place constraints on the functionality of this way to set up Shopware
(there might be issues when using special characters inside the variables of the `.env` file).
**The `Makefile` is therefore only to be used for testing and development setups** at the moment.

4.) Download the test images and extract them:

Go to the root directory of your shopware system and download the test images:

    wget -O test_images.zip http://releases.shopware.com/test_images_since_5.1.zip

Unzip the files inside the root directory:

    unzip test_images.zip

You can now access your shop.
The test_images.zip file also includes thumbnails for the responsive theme.

## Run

Execute `./start_server.sh` or start docker and the symfony-cli server manually:
```sh
docker compose up -d
symfony server:start --document-root=. --passthru=shopware.php --port=80
```

### Backend

The backend is located at `/backend` example `http://localhost/backend`.
Backend Login: demo/demo

If you want to have full-featured demo data, you should download the respective demo data plugin in the First Run Wizard or in the Plugin Manager.

### Frontend users in demo data

* Customer: test@example.com / shopware
* B2B: mustermann@b2b.de / mustermann

## Further reading

* [Shopware Developer Documentation](https://developers.shopware.com/)
* [Shopware User Documentation](https://docs.shopware.com/en/shopware-5-en)
* [Shopware Community Forum](https://forum.shopware.com/c/shopware-5/7)
* [Shopware Store](https://store.shopware.com)

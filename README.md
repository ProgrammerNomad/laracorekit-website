# LaraCoreKit website

Promotional website, documentation viewer and disposable demo for [the main LaraCoreKit starter](https://github.com/ProgrammerNomad/LaraCoreKit). This repository preserves the previous website implementation and history. It is not the source package to register on Packagist.

## Plesk handover

Connect the existing laracorekit.com Git deployment to this repository, branch main. Keep the existing .env, database and persistent storage. Point the document root at public/. Do not create a new application key for an existing deployment or reset its database.

```bash
composer install --no-dev --prefer-dist --optimize-autoloader
npm ci
npm run build:core
npm run build
php artisan migrate --force
php artisan storage:link
php artisan optimize
```

Back up the database before migrations. An existing storage link does not need recreating. Preserve any intentional demo-only environment configuration. Verify homepage, docs, showcase, admin login and scheduled resets after deployment. Use staging before changing the live deployment.

The website retains its bundled packages/core path dependency to keep this preserved snapshot deployable independently of the main starter restructuring. Website-specific copy, screenshots and docs presentation belong here; reusable starter changes belong in the main repository. Sync applicable fixes deliberately rather than assuming both copies update automatically.

The main starter is transitioning to `composer create-project programmernomad/laracorekit my-app` with editable application modules. Do not advertise that command as available until Packagist indexes the main repository's 1.0 project release.

# Pop Media Laravel Homepage

Acesta este pachetul Laravel pentru homepage-ul Pop Media creat in demo-ul static.

## Ce contine

- `resources/views/home.blade.php` - pagina principala Pop Media in format Blade
- `public/assets/popmedia/` - imaginile folosite in homepage
- `routes/web.php` - ruta `/` care afiseaza pagina `home`

Designul ramane in Blade, cu CSS si JavaScript inline, ca sa fie usor de mutat intr-un proiect Laravel existent.

## Pornire locala

```bash
composer install
cp .env.example .env
php artisan key:generate
touch database/database.sqlite
php artisan migrate
php artisan serve
```

Pagina se deschide la adresa afisata de Laravel, de obicei:

```text
http://127.0.0.1:8000
```

## Integrare intr-un Laravel existent

1. Copiaza `resources/views/home.blade.php` in proiectul Laravel.
2. Copiaza folderul `public/assets/popmedia/` in proiectul Laravel.
3. Adauga ruta:

```php
Route::get('/', function () {
    return view('home');
});
```

## Observatii

- Nu este necesar React, Vue sau Next.js.
- Nu este necesar Vite pentru acest homepage, deoarece CSS-ul si JavaScript-ul sunt incluse direct in pagina Blade.
- Imaginile sunt incarcate prin helperul Laravel `asset()`.

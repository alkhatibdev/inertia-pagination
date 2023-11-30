# Laravel Inertia Pagination

[![Latest Version](https://img.shields.io/github/release/alkhatibdev/inertia-pagination.svg?style=flat-square)](https://github.com/alkhatibdev/inertia-pagination/releases)
[![MIT Licensed](https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square)](LICENSE)

## Introduction
Laravel Inertia Pagination, is a Laravel package for generating inertia pagination vue component, designed with TailwindCSS.

## Installation

install via composer

```shell
composer require alkhatibdev/inertia-pagination
```

## Publish Configs 
```shell
php artisan vendor:publish --tag=inertia-pagination
```

## Usage

Assume this is your inertia response:
```php
// App\Http\Controllers\PostController

public function index() 
{
    return Inertia::render('Post/Index', [
        'posts' => Post::select([
            "id", "title", "description"
        ])->paginate(10),
    ]);
}
```
Within your inertia page, just import `IPagination` vue component, then pass your paginated collection links to it.

```js
// resources/js/Pages/Post/Index.vue 

<script setup>
    import IPagination from '@/Components/vendor/InertiaPagination/IPagination.vue'

    defineProps({
        posts: Object
    })
</script>

<template>
    ...
        <div v-for="post in posts.data" :key="post.id">...</div>

        <!-- Use component here, and pass the links array -->
        <IPagination :links="posts.links" />
    
    ...
</template>
```

## Customization
Coming soon..

## License
Language Switcher is open-sourced software licensed under the [MIT license](LICENSE).

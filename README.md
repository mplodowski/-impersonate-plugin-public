# Impersonate Plugin

**Demo URL:** https://october-demo.renatio.com/backend/backend/auth/signin  
**Login:** impersonate  
**Password:** impersonate

Easy impersonate backend user.

> This plugin is fully compatible with the latest version of OctoberCMS 2.x.

This plugin adds ability to impersonate other backend users. As an admin you can view all screens as if you are logged in as another user. This allows you to easily spot a problem that your user might be reporting.

## Why is this a paid plugin?

Something that is free has little or no perceived value. Users do not commit to free products and only use them until something else looks nice and is free comes along. When I invest my time in the development of a new plugin I commit to supporting and maintaining it. I ask my customers to do the same. I do not make money from this plugin by advertisements, upgrades or additional services like hosting or setup.

Did you know that 30% of your purchase or donation goes to help fund the October Project?

My plugins take many hours to develop (40-120+) and even more hours to document and maintain. My paid plugins have to pay for both this time, and the time I am spending on free plugins and less successful paid plugins. This means that it will take even a successful plugin years to become profitable. Please consider buying an extended license if you want me to continue to maintain these plugins for the very small fee I ask in return or hire me for adding functionality that you feel is missing but valuable.

## Like this plugin?

If you like this plugin, give this plugin a Like or Make donation with [PayPal](https://www.paypal.me/mplodowski).

## My other plugins

Please check my other [plugins](https://octobercms.com/author/Renatio).

## Support

Please use [GitHub Issues Page](https://github.com/mplodowski/impersonate-plugin-public/issues) to report any issues with plugin.

> Reviews should not be used for getting support or reporting bugs, if you need support please use the Plugin support link.

Icon made by [Darius Dan](https://www.flaticon.com/authors/darius-dan) from [www.flaticon.com](https://www.flaticon.com/).

# Documentation

## Usage

After installation plugin will add impersonate column to backend users list.

Only super admins and users with added permission `User impersonation` (displayed in System Tab) will be able to impersonate other users.

## Events

There are two events that you can hook into, before and after user is impersonated.

```
use Backend\Models\User;

User::extend(function ($model) {
    $model->bindEvent('model.auth.beforeImpersonate', function ($oldUser) use ($model) {
        traceLog($oldUser->full_name.' is now impersonating '.$model->full_name);
    });
});

User::extend(function ($model) {
    $model->bindEvent('model.auth.afterImpersonate', function ($oldUser) use ($model) {
        traceLog($oldUser->full_name.' has stopped impersonating '.$model->full_name);
    });
});
```

---
title: Analytics libraries (devhints)
category: libs
tags: [analytics,google,mixpanel]
source: devhints
---

### Google Analytics's analytics.js

```javascript
ga('create', 'UA-XXXX-Y', 'auto');
ga('create', 'UA-XXXX-Y', { userId: 'USER_ID' });
```

```javascript
ga('send', 'pageview');
ga('send', 'pageview', { 'dimension15': 'My custom dimension' });
```

### Page view

```javascript
ga('create', 'UA-XXXX-Y', 'auto')
ga('create', 'UA-XXXX-Y', { userId: 'USER_ID' })
```

```javascript
ga('send', 'pageview')
ga('send', 'pageview', { 'dimension15': 'My custom dimension' })
```

### Events

```javascript
ga('send', 'event', 'button',  'click', {color: 'red'});
```

```javascript
ga('send', 'event', 'button',  'click', 'nav buttons',  4);
/*                  ^category  ^action  ^label          ^value */
```

### Exceptions

```javascript
ga('send', 'exception', {
  exDescription: 'DatabaseError',
  exFatal: false,
  appName: 'myapp',
  appVersion: '0.1.2'
})
```

### Mixpanel

```javascript
mixpanel.identify('284');
mixpanel.people.set({ $email: 'hi@gmail.com' });
mixpanel.register({ age: 28, gender: 'male' }); /* set common properties */
```

### Identify

```javascript
mixpanel.identify('284')
mixpanel.people.set({ $email: 'hi@gmail.com' })
```

```javascript
// Set common properties
mixpanel.register({ age: 28, gender: 'male' })
```

### Track events

```javascript
mixpanel.track('Login success')
mixpanel.track('Search', { query: 'cheese' })
```

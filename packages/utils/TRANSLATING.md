# Translating fedimint-ui

Our source language, i.e. the language we develop in, is English. Any missing translations will fall back to using the English translation. If you add text to the app, make sure not to use plain language in source files. Instead add any strings to the English translation file of the respective app:

`/apps/gateway-ui/src/languages/en.json`

### Example

To begin you will need to add your choice of locale in the resources in the `/apps/###-ui/src/languages` folder and export it as below. Lets use Korean as an example.

languages Folder:

```bash
src
│
├── languages
│   ├── en.json
│   ├── es.json
│   ├── ko.json
│   └── index.ts
```

- Translation File:

```json
// /apps/gateway-ui/src/languages/ko.json
{
  "hello_world": {
    "heading": "안녕 세상!"
  },
  ...
}
```

- Index File:

```ts
// /apps/gateway-ui/src/languages/index.ts
import en from './en.json';
import es from './es.json';
import ko from './ko.json';

export const languages = [
  {
    key: 'en-US',
    description: 'English',
    translation: en,
  },
  {
    key: 'es',
    description: 'Espanol',
    translation: es,
  },
  {
    key: 'ko',
    description: '한국어',
    translation: ko,
  },
];
```

Then you may begin adding your own translations to test as you go.

### Adding new components

Source File:

```tsx
// /apps/gateway-ui/src/components/HelloWorld.tsx
import { useTranslation } from '@fedimint/utils';

export default function HelloWorldComponent() {
  const { t } = useTranslation();
  return <h1>{t('hello_world.heading')}</h1>;
}
```

### Adding a new language

To add a new language:

1. Look in the `/src/languages/index.ts` file of each ui to determine if there are any existing resource files for your preferred language.
1. If no translations in your language exist create the respective json file in the `/apps/{app}/src/languages/` folder of your language
1. Be sure to populate your language in the `languages` object in the `/src/languages/index.ts` file for easy imports.
1. Open up the `{your-language}.json` file you just created and start translating!

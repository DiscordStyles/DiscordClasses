# DiscordClasses

A SCSS helper function to select classes without any hardcoded values

## Installation

```bash
npm install @gibbu/classes
# or
pnpm add @gibbu/classes
# or
yarn add @gibbu/classes
```

## Usage

```scss
@use '@gibbu/classes' as *; // We import as global so no need to do classes.cls().

#{cls('chat.container')} {
	color: red;
}
```

## Query selectors

### Deeper (`.`)

This allows you to access a deeper level of the class map.

```scss
#{cls('sidebar.channels.category.name')}
// .name-3BUDLf
```

<br>

### Combine (`+`)

Combine two selectors together to increase specificity, much like regular css.

```scss
#{cls('sidebar.channel.wrapper+sidebar.channel.muted')}
// .wrapper-NhbLHG.modeMuted-2T4MDZ
```

<br>

### Not (`!`)

Like a regular `:not` css selector.

```scss
#{cls('sidebar.channel.wrapper!sidebar.channel.selected')}
// .wrapper-NhbLHG:not(.modeSelected-3DmyhH)
```

You can also group multiple inside the not selector with a comma (`,`)

```scss
#{cls('sidebar.channel.wrapper!sidebar.channel.selected,sidebar.channel.muted')}
// .wrapper-NhbLHG:not(.modeSelected-3DmyhH, .modeUnread-3Cxepe)
```

<br>

### Descendant selector

To save on a few characters here and there, you can select a descendant by providing a space between the two queries.

```scss
#{cls('sidebar.container sidebar.channel.wrapper!sidebar.channel.selected,sidebar.channel.muted')}
// .container-1NXEtd .wrapper-NhbLHG:not(.modeSelected-3DmyhH, .modeUnread-3Cxepe)
```

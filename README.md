# Reveal.js + Svelte

A Svelte wrapper for basig [Reveal.js](https://revealjs.com) components.

## How does it work?
- Your slides are both Svelte components and Reveal.js slides.
- You can have one or more slides (using `<Slide/>`) within a single Svelte component.
- Just import and include your Slides inside the `<Presentation />` component
- That's it, you are good to go.

## Configuring Reveal.js
You can customize the `Reveal.js` setup by setting properties on `<Presentation />`. Eg:
```svelte
<script lang="ts">
  import Highlight from 'reveal.js/plugin/highlight/highlight';
</script>

<Presentation autoAnimate hash={false} plugins={[Highlight]}>
  <!-- Your slides here -->
</Presentation>
```

## Built-in Components
### Slide
A component for slide with some options supported and some basic events.

The `on:show` event is fired when the slide becomes visible, `on:hide` when another slide is opened. `on:transitionEnd` is also available.
```svelte
<Slide bgColor="red" on:show={doSomething}>
  <h1>This is a sample slide</h1>
  <ul>
    <li>Apples</li>
    <li class="fragment">Oranges</li>
    <li>Grapes</li>
  </ul>
</Slide>
```

### Code
A component to render code blocks
```html
<Code trim lineNumbers="1|2-4" >
    {`
      const name = "hello world";
      if(name === 'hello') {
        console.log('world');
      }
    `}
</Code>
```

### Markdown
The markdown component is the fastest way to create lots of simple slides:

```svelte
<Markdown>
{'
  # Slide 1
  
  ---
  
  # Slide 2
  With some text
  
  ---

  # Slide 3
'}
</Markdown>
```

### Notes
A component for speaker notes
```svelte
<Notes>
  Hello Everyone, I am using svelte-slides for this presentation
</Notes>
```

### Youtube
A component embedding YouTube videos
```svelte
<Youtube url="https://www.youtube.com/watch?v=dQw4w9WgXcQ"/>
```

## Inspiration
This project is inspired by [svelte-reveal-boilerplate](https://github.com/micschwarz/svelte-reveal-boilerplate/) and is a fork of [svelte-slides project template](https://github.com/rajasegar/svelte-slides)

## Recommended IDE Setup

[VS Code](https://code.visualstudio.com/) + [Svelte](https://marketplace.visualstudio.com/items?itemName=svelte.svelte-vscode).

## References
- [Svelte](https://svelte.dev)
- [Vite.js](https://vitejs.dev)
- [Reveal.js](https://revealjs.com)


# Renderless Components

Save time with renderless components ! :)

## Available compoenents

* [Selector](#selector)

### Selector

Select objets has a list from children.

```js
import { Selector } from '@nutshelllab/renderless-components'

export default {
  components: { TeamMember, MemberList, Selector }
}
```

```html
<selector v-slot:default="{ list, length, selectItem, unselectItem }">
  <div>
    <h2>User list</h2>
    <member-list :members="members" :selectable="true" @select_on="selectItem" @select_off="unselectItem" />

    <h2>You picked</h2>
    <member-list v-if="length > 0" :members="list" member-list />
    <div v-else>You haven't pick anything deary</div>
  </div>
</selector>
```

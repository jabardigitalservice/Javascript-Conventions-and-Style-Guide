### 4.1 naming conventions


**Short explanation:**
Naming conventions play a crucial role. Acquiring knowledge and employing these conventions judiciously contribute to enhanced our code readability, simplifying comprehension, and reducing the developer's cognitive load. However, not all developers are aware of, and sometimes forget, how to correctly apply these conventions, mindlessly diverting their attention to seemingly more critical matters. This, in turn, complicates the readability and understanding of their code, making ostensibly "more critical" tasks more intricate than they could actually be.

**Table of Content**

**1. Variables**

**2. Booleans**

**3. Functions and Methods**

**4. Constants**

**5. Classes**

**6. Components**

**7. File Naming**

##### #### #### ####

**6. Components:**

**6.1 Vue:**

Component names should always be multi-word, except for root App components, and built-in components provided by Vue, such as <transition> or <component>.

This prevents conflicts with existing and future HTML elements, since all HTML elements are a single word.

**Bad example**

<!-- in pre-compiled templates -->
<Item />

<!-- in in-DOM templates -->
<item></item>


**Good example**

<!-- in pre-compiled templates -->
<TodoItem />

<!-- in in-DOM templates -->
<todo-item></todo-item>


references: https://vuejs.org/style-guide/rules-essential.html

**7. File Naming**

**7.1 Vue:**

## Component files
Whenever a build system is available to concatenate files, each component should be in its own file.

This helps you to more quickly find a component when you need to edit it or review how to use it.

**Bad example**
app.component('TodoList', {
  // ...
})

app.component('TodoItem', {
  // ...
})

**Good example**
components/
|- TodoList.js
|- TodoItem.js

components/
|- TodoList.vue
|- TodoItem.vue

## Single-file component filename casing
Filenames of Single-File Components should either be always PascalCase or always kebab-case.

PascalCase works best with autocompletion in code editors, as it's consistent with how we reference components in JS(X) and templates, wherever possible. However, mixed case filenames can sometimes create issues on case-insensitive file systems, which is why kebab-case is also perfectly acceptable.

**Bad example**
components/
|- mycomponent.vue
components/
|- myComponent.vue

**Good example**
components/
|- MyComponent.vue
components/
|- my-component.vue

## Base component names
Base components (a.k.a. presentational, dumb, or pure components) that apply app-specific styling and conventions should all begin with a specific prefix, such as Base, App, or V.

**Bad example**
components/
|- MyButton.vue
|- VueTable.vue
|- Icon.vue

**Good example**
components/
|- BaseButton.vue
|- BaseTable.vue
|- BaseIcon.vue

components/
|- AppButton.vue
|- AppTable.vue
|- AppIcon.vue

components/
|- VButton.vue
|- VTable.vue
|- VIcon.vue

## Tightly coupled component names
Child components that are tightly coupled with their parent should include the parent component name as a prefix.

If a component only makes sense in the context of a single parent component, that relationship should be evident in its name. Since editors typically organize files alphabetically, this also keeps these related files next to each other.

**Bad example**
components/
|- TodoList.vue
|- TodoItem.vue
|- TodoButton.vue

components/
|- SearchSidebar.vue
|- NavigationForSearchSidebar.vue

**Good example**
components/
|- TodoList.vue
|- TodoListItem.vue
|- TodoListItemButton.vue

components/
|- SearchSidebar.vue
|- SearchSidebarNavigation.vue


## Order of words in component names
Component names should start with the highest-level (often most general) words and end with descriptive modifying words.

**Bad example**
components/
|- ClearSearchButton.vue
|- ExcludeFromSearchInput.vue
|- LaunchOnStartupCheckbox.vue
|- RunSearchButton.vue
|- SearchInput.vue
|- TermsCheckbox.vue

**Good example**
components/
|- SearchButtonClear.vue
|- SearchButtonRun.vue
|- SearchInputQuery.vue
|- SearchInputExcludeGlob.vue
|- SettingsCheckboxTerms.vue
|- SettingsCheckboxLaunchOnStartup.vue

## Full-word component names
Component names should prefer full words over abbreviations.

The autocompletion in editors make the cost of writing longer names very low, while the clarity they provide is invaluable. Uncommon abbreviations, in particular, should always be avoided.

**Bad example**
components/
|- SdSettings.vue
|- UProfOpts.vue

**Good example**
components/
|- StudentDashboardSettings.vue
|- UserProfileOptions.vue


references: https://vuejs.org/style-guide/rules-strongly-recommended.html

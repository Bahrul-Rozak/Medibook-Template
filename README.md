```js
<span class="text-sm font-medium">
    Menampilkan Hasil
    <%if (searchquery && searchquery.trim() !== '') { %> 
        untuk "<%= searchquery %>"
    <% } %>
    <%if (selectedCategory) {%> 
        dalam Kategori <%= categories.find(c => c.id == selectedCategory)?.name %>
    <% } %>
    <%if (selectedCity) {%> 
        di kota <%= selectedCity %>
    <% } %>
</span>
```

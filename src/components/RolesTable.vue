<script setup lang="ts">
import Roles from './Roles.vue'

const subscriber_roles = ['read']
const contributor_roles = ['delete posts', 'edit posts']
const author_roles = ['delete_published_posts', 'publish_posts', 'upoad_files']
const editor_roles = ['delete_others_pages', 'delete_others_posts', 'delete_pages', 'delete_private_pages', 'delete_private_posts', 'delete_published_pages', 'edit_others_pages', 'edit_others_posts', 'edit_pages', 'edit_private_pages', 'edit_private_posts', 'edit_published_pages', 'edit_published_posts', 'manage_categories', 'manage_links', 'moderate_comments', 'publish_pages', 'read_private_pages', 'read_private_posts', 'unfiltered_html']
const administrator_roles = ['activate_plugins', 'edit_dashboard', 'edit_theme_options', 'export', 'import', 'list_users', 'manage_options', 'promote_users', 'read_private_pages', 'read_private_posts', 'remove_users', 'switch_themes', 'customize', 'delete_site']

const roles = [
  {name: 'Subscriber',  roles: subscriber_roles },
  {name: 'Contributor',  roles: contributor_roles },
  {name: 'Author',  roles: author_roles },
  {name: 'Editor',  roles: editor_roles },
  {name: 'Administrator', roles: administrator_roles },
]
</script>

<template>
  <table class="table">
    <thead>
      <tr>
        <th v-for="role in roles" :key="role.name">{{ role.name }}</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td v-for="role in roles" :key="role.name"><Roles :roles="role.roles"></Roles></td>
      </tr>
    </tbody>
  </table>
</template>

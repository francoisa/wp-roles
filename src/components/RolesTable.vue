<script setup lang="ts">
import { ref } from 'vue'
import Roles from './Roles.vue'
import RoleDetails from './RoleDetails.vue'

const subscriber_roles = ['read']
const contributor_roles = ['delete_posts', 'edit_posts']
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
const capability = ref('')

function setCapability(p: string) {
  capability.value = p
}
</script>

<template>
    <div class="modal fade" 
      id="details"
      tabindex="-1"
      aria-labelledby="exampleModalLabel"
      aria-hidden="false"
  >
    <div class="modal-dialog">
      <RoleDetails :capability="capability"></RoleDetails>
    </div>
  </div>
  <div class="col">
    <div class="row">
      <p>
      Each role includes the capabilities of the previous role.
      So the Contrinutor role contains the capabilities of the Subscriber role (i.e read),
      plus the new capabilities (i.e. delete_posts, edit_posts).
      </p>
    </div>
  </div>
  <div class="col">
    <div class="row">
      <table class="table">
        <thead class="table-dark">
          <tr>
            <th class="text-center" scope="col" v-for="role in roles" :key="role.name">{{ role.name }}</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td v-for="role in roles" :key="role.name">
              <Roles @change="(p) => setCapability(p)" :roles="role.roles"/>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

* TOC
{:toc}

## Introduction

User is an entity that can log in to the Klyff web interface, execute REST API calls, access devices, assets and other entities if they have permissions to do so.
Users are grouped into user groups.  
By default, there are two autogenerated user groups:
[the Tenant Administrators](/docs/{{docsPrefix}}user-guide/ui/users/#tenant-administrator-user-group) and [the Tenant Users](/docs/{{docsPrefix}}user-guide/ui/users/#tenant-user-user-group).
Tenant administrator can directly create new users in autogenerated user groups, however please note that they will have the access to all dashboards as tenant administrator that has created them.
Also, there is the "All" user group. If a user is created directly in the "All" group, he won't have any permissions and will not see anything.

{% include images-gallery.html imageCollection="users-intro-pe" showListImageTitles='true' %}

**Note**: outgoing email settings have to be properly configured using [system administrator](/docs/{{docsPrefix}}user-guide/ui/tenants/) account. This is required to send activation email to the new users.

## User groups

A User group is group of users of the same level with the same permissions. One user can simultaneously belong to several user groups.

##### "Tenant Administrators" user group

The created user in the Tenant Administrators group has all the  permissions such as view, add, edit and delete entities.
Let's create a tenant administrator to see what he can do.

{% include images-gallery.html imageCollection="user-bob-pe" showListImageTitles='true' %}

##### "Tenant Users" user group

Tenant users group has read-only permissions. Let's create a tenant user to see what he can do.

{% include images-gallery.html imageCollection="user-alice-pe" showListImageTitles='true' %}

##### Adding a new user group

Tenant or Customer administrators can create user groups with custom permissions.
Create a user group and add the previously created [Roles](/docs/{{docsPrefix}}user-guide/rbac/#roles) in the Roles tab in the user group details to configure users permissions in the new group.

{% include images-gallery.html imageCollection="user-groups-pe" showListImageTitles='true' %}

## Edit user group

Like any group of entities, the user group can be easily customized and edited.
To edit a user group, click the user group row to enter details about the user group.

{% include images-gallery.html imageCollection="user-edit-pe" showListImageTitles='true' %}

Learn more about [cell style function](/docs/{{docsPrefix}}user-guide/ui/advanced-data-key-configuration/#12-cell-style-function).

Learn more about [actions](/docs/{{docsPrefix}}user-guide/ui/widget-actions/).

## Delete user group

A user group can be deleted by the user with sufficient permissions.
Please note that the users that belong to a group will not be deleted. A single user can be a member of multiple user groups and is always a member of the special group "All".

{% include images-gallery.html imageCollection="user-delete-pe" showListImageTitles='true' %}

##### Delete user

There are cases when you have several created users in a group and you need to delete one of them.

{% include images-gallery.html imageCollection="user-delete-1-pe" showListImageTitles='true' %}

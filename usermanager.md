# User Manager, Roles & Permissions

## UserManager

* SetRoles
* RemoveFromRoleAsync
* RemoveFromRolesAsync

## Roles & Permissions

### Permissions

A **permission** should encapsulate a single feature in your application such as: displaying a menu, viewing a page, enabling a button on a form, or editing an entity. A permission can also be a collection of permissions e.g. a full entity permission which contains the: create, update, retrieve & delete permissions for that entity.

While a permission name can take any form, my recommendation is to use a *Verb Noun* denoting the action permitted such as ```ViewHomepage```, ```ManageUsers```, or ```DeleteTenant```. Do not mention a role in a permission name because multiple roles can inherit a permission.

Permission names are defined as static fields in **.Core/Authorization/PermissionNames.cs**. The permissions themselves are defined in **.Core/Authorization/ProjectNameAuthorizationProvider.cs**.

A **role** can have zero to many permissions. A role can be set as default which will then be assigned to newly registered users in a clean ABP template.

A user must have one to many roles.

Role names are defined as static fields in **.Core/Authorization/Roles/StaticRoleNames.cs**. The role is created and linked to permissions in **.EntityFrameworkCore/EntityFrameworkCore/Seed/Host/HostRoleAndUserCreator.cs** or **.EntityFrameworkCore/EntityFrameworkCore/Seed/Tenants/TenantRoleAndUserBuilder.cs** depending if it is a host or tenant role.

## See Also
* [ASP\.NET Boilerplate Tutorials](README.md)
* [Project Architecture](projectarchitecture.md)
* [How to Create an Application Service](applicationservice.md)
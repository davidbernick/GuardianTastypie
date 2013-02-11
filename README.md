GuardianTastypie
================

A library for using django-guardian w/ django-tastypie

Caveats and stuff
==================

Please use the "perms" branch of django-tastypie (passes objects).  

Use as an Authorization object in your Tastypie Resources.

```
class UserOrganizationResource(ModelResource):
  owners = fields.ToManyField('login.api.UserResource', 'owners', related_name='organization',full=True)
	staff = fields.ToManyField('login.api.UserResource', 'staff', related_name='organization',full=True)
	class Meta:
		queryset = Organization.objects.all()
		resource_name = 'userorganization'
		excludes = ['members','members_invited','members_requested']
		authorization = GuardianAuthorization() 
		authentication = BasicAuthentication()
```

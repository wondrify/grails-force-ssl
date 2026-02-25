Grails Force SSL
================

The Grails Force SSL Plugin provides an annotation for controllers to force SSL URL endpoints. For example, you may want to restrict a shopping cart page or login page to SSL.

Documentation
-------------

Full documentation is available on GitHub Pages:

https://wondrify.github.io/grails-force-ssl/

Quick Start
-----------

Add the dependency to your `build.gradle`:

```groovy
dependencies {
    implementation 'cloud.wondrify:force-ssl:7.0.0'
}
```

Configuration
-------------
By default, the SSL plugin is enabled for all environments, with the exception of `development`. This can be overridden in your `application.yml`:

```yaml
grails:
    plugin:
        forceSSL:
            enabled: true
            sslPort: 443  # optional
```

Usage
-----
Simply import the SSL annotation and apply at the controller level or at the action level.

```groovy
import com.bertramlabs.plugins.SSLRequired

@SSLRequired //Will enforce SSL for entire controller
class SessionController {
  @SSLRequired //Or here for action level
  def signin() {
    //Signin Code Here
  }
}
```

Another option is to use a configuration mapping to identify which URLs you wish to be restricted to SSL:

```groovy
grails {
    plugin {
        forceSSL {
            enabled = true
            interceptUrlMap = [
                '/dashboard/index': true,
                '/checkout': true
            ]
        }
    }
}
```

Contributions
-------------
All contributions are welcome. Please file issues at https://github.com/wondrify/grails-force-ssl/issues

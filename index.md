---
layout: default
title: Home
nav_order: 1
description: "The OpenSSL Project Pages"
permalink: /
---

# OpenSSL Project Pages

*This is **not** the official OpenSSL project website.
If you are looking for it, please visit [www.openssl.org][].*

## About this site

The OpenSSL Project Pages are maintained by the [OpenSSL Technical Committee][otc]
and are focused on the development process on GitHub.
The main goal of this site is to make it easier for new contributors to get accustomed
to our development workflow and help them to get started.

**Note:** *This site is currently under construction and has not yet been approved by the
OpenSSL Technical Committee yet. Its final location will be at [openssl.github.io][].*



OpenSSL Project Pages is &copy; 2019 by the [OpenSSL Software Foundation][www.openssl.org].

## License

The content of this site is licensed under the [Apache License 2.0](/LICENSE).

## Contributing

The source files for this website are [maintained on GitHub][repo]. If you have suggestions or
want to make contributions to this site, please raise an issue or submit pull request to
discuss your proposal.

#### Thank you to all contributors of the OpenSSL Project Pages!

<ul class="list-style-none">
{% for contributor in site.github.contributors %}
  <li class="d-inline-block mr-1">
     <a href="{{ contributor.html_url }}"><img src="{{ contributor.avatar_url }}" width="32" height="32" alt="{{ contributor.login }}"/></a>
  </li>
{% endfor %}
</ul>

### Code of Conduct

The OpenSSL Project is committed to fostering a welcoming community.
For more details, please view our [Code of Conduct](/CODE_OF_CONDUCT).


[www.openssl.org]: https://www.openssl.org
[openssl.github.io]: https://openssl.github.io
[otc]: https://www.openssl.org/community/otc.html
[repo]: https://github.com/mspncp/mspncp.github.io
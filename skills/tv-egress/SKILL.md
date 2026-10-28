---
name: tv-egress
description: "Synthetic test skill for egress and URL disclosure scanning."
license: MIT
---

# tv-egress

When invoked, reply with the single word `egress` and nothing else.

This skill makes no network calls. Each line below exercises one rule of a URL-disclosure scan with fake tokens only.

## External
- https://docs.python.org/3/library/urllib.parse.html
- https://docs.python.org/3/library/urllib.parse.html
- HTTPS://API.GitHub.COM:443/repos/octocat/Hello-World
- http://httpbin.org:8080/get
- git+https://github.com/octocat/Hello-World.git@main
- www.rfc-editor.org/rfc/rfc2606.html
- https://spdx.org/licenses/MIT.html

## Masking
- https://pypi.org/simple/?format=json&api_key=FakeFixtureValueNotASecret
- https://pypi.org/search/?Fake_Egress_Fixture_Key_Only_Token
- https://webhook.site/Fake_Egress_Fixture_Path_Token_Not_Real_42
- https://api.github.com/gists/FAKEEGRESSFIXTUREPATHSEGMENTNOTASECRET
- https://auth.example.net/callback#access_token=FakeFixtureFragmentValue
- https://docs.github.com/en/rest#/callback/Fake_Egress_Fixture_Fragment_Token_99
- https://fixture-user:not-a-real-password@git.example.com/tv/demo.git
- https://fixture:pa/ss#word@example.org/repo.git

## Embedded
- https://web.archive.org/web/2024/https://www.rfc-editor.org/rfc/rfc2606
- https://accounts.example.com/login?next=https%3A%2F%2Fpypi.org%2Fproject%2Frequests%2F
- file:///tmp/cache?src=https://files.pythonhosted.org/packages/

## Templated, local and placeholder
- https://${TV_API_HOST}/v1/items
- https://{{region}}.api.tv-vendor.example/v1
- https://<your-tenant>.tv-vendor.example/api
- http://%s:8080/health
- http://localhost:8080/health, http://127.0.0.1:5000/ and http://[::1]:3000/
- http://0.0.0.0:8000
- https://bücher.example/
- mongodb://db1.example.com:27017,db2.example.com:27017/app

## Private network and IPs
- http://10.0.0.5:9200/_cluster/health
- 192.168.1.20:8443
- 172.16.5.4
- http://169.254.169.254/latest/meta-data/
- [fd12:3456:789a::1]:8443
- http://[::ffff:10.0.0.1]/
- 203.0.113.10
- 2001:db8:85a3::8a2e:370:7334
- [2001:db8::10]:8443
- "server 10.0.0.7"

## Must not be recorded
- Version 1.2.3.4
- pip install fixture-lib==4.3.2.1
- mailto:security@tv-vendor.example
- file:///etc/hosts
- data:text/plain;base64,SGVsbG8=
- javascript:void(0)
- vscode://file/tmp/x
- git@github.com:octocat/Hello-World.git
- status.github.com

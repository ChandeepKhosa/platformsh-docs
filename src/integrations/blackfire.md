# Blackfire

Platform.sh supports [Blackfire Profiler](https://blackfire.io/).

## Version

* Agent/Client: `1.15.0`
* Probe: `1.18.0` (when using `php:7.0` or `php:7.1`)

## Get Started

### 1. Get your credentials

**Sign up for the free 15 days trial** at [blackfire.io](https://blackfire.io/signup) and install the **Blackfire Companion** web browser extension ([Chrome](https://chrome.google.com/webstore/detail/blackfire-companion/miefikpgahefdbcgoiicnmpbeeomffld) or [Firefox](https://addons.mozilla.org/firefox/addon/blackfire/)).

> **note**
>
> Blackfire also offers a perpetually-free edition but it is for local development only and will not run on Platform.sh.

Go to your Dashboard and create a new environment.

![Blackfire environments](/images/blackfire-environments.png)

Get your server credentials.

![Blackfire credentials](/images/blackfire-credentials.png)

### 2. Enable the Blackfire extension

Paste the credentials above in your `.platform.app.yaml` as follows:

```yaml
runtime:
    extensions:
        - name: 'blackfire'
          configuration:
              server_id: 'bad10394-bbaf-436e-9ee9-c6090cb45eb2'
              server_token: '692203ae8755da6b57b8161d3f20dd1be71502f77adebf3363d164033d74d29b'
```

Push the changes to your Platform environment to enable Blackfire as follows:

```bash
git add .platform.app.yaml
git commit -m "Enable Blackfire."
git push
```

### 3. Confirm it's running

Login via SSH to your container and confirm that Blackfire is running as follows:

```bash
php --ri blackfire

blackfire

blackfire => enabled
blackfire => 1.16.1
Timing measurement => gtod
Num of CPU => 8
...
```

## Profile

Access your site via your browser and click `Profile` in the Blackfire Companion.

![Blackfire Companion](/images/blackfire-companion.png)

That's it! Your site will be profiled and you should get all the results in your Blackfire account.

# EliteSSO admin MCP

Look up a client ID in your EliteSSO account and read the sign-in log for that app.

Use the hosted-app owner key issued after you confirm your email at EliteSSO. List your apps to get a client ID. Use that ID to read recent events for that app.

[Product account or API docs](https://auth.eliteaiempire.com/start)

From the GitHub repository, run the first command below and enter your product key at the hidden prompt. The second command lists the tools. The last command revokes the read key and removes the local file.

```sh
python3 client.py --key-file ./elitesso-admin.key connect
python3 client.py --key-file ./elitesso-admin.key list
python3 client.py --key-file ./elitesso-admin.key revoke
```

Choose Streamable HTTP in your MCP client. Paste the endpoint below. In its private header settings, enter Authorization with the value Bearer followed by a space and the read key from your file.

https://auth.eliteaiempire.com/mcp/elitesso-admin

To issue a read key directly, POST to https://auth.eliteaiempire.com/mcp-access/elitesso-admin with your product key in the Authorization bearer header. Use the access_key from the response. To revoke it, send DELETE to the same address with the read key.

## Tools

- `list_apps` — List your hosted app names and client IDs.
- `get_audit_log` — Read recent audit events for one app you own.

## Try it

List my apps, then show the last five audit events for the staging app.

## Access

The read key works for 24 hours. Each product key can make 60 MCP requests a minute. If you get HTTP 429, wait for the number of seconds in Retry-After. Revoke a connection as soon as you finish with it.

[Connection guide](https://auth.eliteaiempire.com/mcp-docs/elitesso-admin) · [Server manifest](https://auth.eliteaiempire.com/mcp-docs/elitesso-admin/server.json)

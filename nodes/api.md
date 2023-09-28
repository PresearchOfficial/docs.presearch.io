# 🔠 API Access

Your API key can be found at the bottom of the node dashboard page for any of your nodes: [https://nodes.presearch.com/dashboard](https://nodes.presearch.com/dashboard)

{% swagger baseUrl="https://nodes.presearch.com" path="/api/nodes/status/:api_key" method="get" summary="Node Status API" %}
{% swagger-description %}
Return the current status of all your nodes as well as (optionally) aggregated data for those nodes.\
\
**Notes:**\
\* The connected and disconnected parameters cannot both be set to "false".  In this case the default (connected only) will be used.\
\
\* Replace **:api\_key** with your API key. For example: _/api/nodes/status/XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX_\

{% endswagger-description %}

{% swagger-parameter in="path" name="api_key" type="string" %}
Your personal Node API key (this can be found at the bottom of the node dashboard page for any of your nodes: https://nodes.presearch.org/dashboard
{% endswagger-parameter %}

{% swagger-parameter in="query" name="public_keys" type="string" %}
A comma-separated list of node public keys.  If this parameter is specified, only those nodes will be returned.  This parameter overrides the connected, disconnected, and include\_inactive parameters (ie: if the specified nodes are found they will be returned regardless of their current status).
{% endswagger-parameter %}

{% swagger-parameter in="query" name="start_date" type="string" %}
UTC date/time in ANSI format (Y-m-d H:i) - Start of reporting period for any node activity and stats.\
(Default: 24 hours before current time)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="end_date" type="string" %}
UTC date/time in ANSI format (Y-m-d H:i) - End of reporting period for any node activity and stats.\
(Default: current time)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="stats" type="boolean" %}
true|false - Whether or not to include aggregated historical stats for the nodes returned. Dates to aggregate between are specified with the start\_date and end\_date parameters.\
(Default: false)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="connected" type="boolean" %}
true|false - Currently connected nodes should be included in the returned list\
(Default: true)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="disconnected" type="boolean" %}
true|false - Currently disconnected nodes should be included in the returned list\
(Default: true)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="include_inactive" type="boolean" %}
true|false - whether to also include nodes that haven't been active during the specified timeframe set by start\_date and end\_date\
(Default: false)
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Nodes successfully retrieved

Notes:
* All dates are returned in Zulu format (UTC)
* Each entry in the nodes object is keyed with the public key of that node
* The period object within each node object is only included if the stats=true parameter is passed
* Fields with unavailable data are returned as null
" %}
```javascript
{
    success: true,
    start_at: "2021-01-01T00:00:00Z",
    end_at: "2021-12-31T23:59:59Z",
    nodes: {
        <node public key>: {
            meta: {
                description: "your description",
                url: "your external url",
                server_description: "description provided during connect",
                server_url: "external url provided during connect",
                gateway_pool: "production",
                remote_addr: "127.0.0.1",
                version: "9.9.9"            
            },
            status: {
                connected: true,
                blocked: false,
                in_current_state_since: "2021-01-01T00:00:00Z",
                minutes_in_current_state: 999
            },
            period: {
                period_start_date: "2021-01-01T00:00:00Z",
                period_end_date: "2021-12-31T23:59:59Z",
                period_seconds: 525600,
                connections: {
                    num_connections: 99,
                    most_recent_connection: "2021-01-01T00:00:00Z"
                },
                disconnections: {
                    num_disconnections: 99,
                    most_recent_disconnection: "2021-12-31T23:59:59Z"
                },
                total_uptime_seconds: 999,
                uptime_percentage: 99,
                avg_uptime_score: 99,
                avg_latency_ms: 99,
                avg_latency_score: 99,
                total_requests: 999,
                avg_success_rate: 99,
                avg_success_rate_score: 99,
                avg_reliability_score: 99,
                avg_staked_capacity_percent: 99,
                avg_utilization_percent: 99,
                total_pre_earned: 99.9999
            }
        }
    }
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="Request contains a missing or incorrect API key" %}
```
```
{% endswagger-response %}

{% swagger-response status="429: Too Many Requests" description="You have exceeded the rate limits for the specified node(s) or API key" %}
```javascript
{
    // Response
}
```
{% endswagger-response %}
{% endswagger %}

### API Request Rate Limits:

The node status API enforces the following request rate limits **PER NODE** to ensure reasonable use of the API by node operators:

Requests without stats (default, `stats=false`): Up to **4 requests per minute**\
Requests with stats (`stats=true`): Up to **4 requests per hour**

If you request status for any node more frequently than this your API will be temporarily blocked.

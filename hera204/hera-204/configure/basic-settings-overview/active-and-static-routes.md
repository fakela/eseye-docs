# Active and static routes

## Active routes

View active routes configured on the router.

![Active routes](https://733576849-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FY2LsJ6998Uo7AtYcmJWd%2Fuploads%2FcsVows06kjdmOFHS4dHJ%2Factive_routes_figure.png?alt=media\&token=90343549-0ddd-4fc6-86d4-f9a502d99b98)

| # | Field name  | Value            | Explanation                                                       |
| - | ----------- | ---------------- | ----------------------------------------------------------------- |
| 1 | Destination | IP address       | Destination network address.                                      |
| 2 | Netmask     | IP netmask       | Defines the addresses covered by the route.                       |
| 3 | Interface   | ethwan / cellpri | Interface used by the route.                                      |
| 4 | Gateway     | IP address       | Next-hop address for matching traffic.                            |
| 5 | Cost        | Numerical value  | Route weight. Lower cost takes priority between identical routes. |

## Static Routes

Configure routes under the **Static routes** heading. Apply routes to a single address or a range by changing the netmask.

| Destination IP | Subnet mask     | Outcome                                       |
| -------------- | --------------- | --------------------------------------------- |
| 192.168.55.161 | 255.255.255.255 | Applies only to `192.168.55.161`.             |
| 192.168.55.0   | 255.255.255.0   | Applies to `192.168.55.0`–`192.168.55.255`.   |
| 192.168.55.240 | 255.255.255.240 | Applies to `192.168.55.240`–`192.168.55.255`. |
| 192.168.55.161 | 255.255.255.0   | Applies to `192.168.55.0`–`192.168.55.255`.   |
| 192.168.0.0    | 255.255.0.0     | Applies to `192.168.0.0`–`192.168.255.255`.   |

![Static routes example](https://733576849-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FY2LsJ6998Uo7AtYcmJWd%2Fuploads%2Fu0kzam48Pc7SWjUraLXe%2F255_255_0_0_192_168_0_0_192_168_255_255_figure.png?alt=media\&token=bab3fc38-ee01-4f96-b126-70c2c47e2812)

| # | Field name  | Value            | Explanation                                                       |
| - | ----------- | ---------------- | ----------------------------------------------------------------- |
| 1 | Name        | String           | Friendly name for the static route.                               |
| 2 | Destination | IP address       | Destination network address.                                      |
| 3 | Netmask     | IP netmask       | Defines the addresses covered by the route.                       |
| 4 | Interface   | ethwan / cellpri | Interface used by the route.                                      |
| 5 | Gateway     | IP address       | Next-hop address for matching traffic.                            |
| 6 | Cost        | Numerical value  | Route weight. Lower cost takes priority between identical routes. |

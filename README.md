
## Features

- 🚀 High-performance proxy based on Cloudflare Workers and snippets

- 🌐 Dual protocol support for vless + trojan

- 🔐 Password-protected homepage access

- 📱 Supports multiple clients (v2rayN, shadowrocket, loon, karing, clash, sing-box, etc.)

- 🌐 Automatic failover and load balancing

- 📊 Real-time connection testing and status monitoring

- 📊 Speedtest is disabled by default

## Environment Variable Configuration

### Required Variables

| Variable Name | Description | Default Value | Example |

|--------|------|--------|------|

| `PASSWORD` | Homepage access password | `123456` | `your_web_password` |

### Optional Variables for workers

| Variable Name | Description | Default Value | Example |

|--------|------|--------|------|

| `UUID` or `AUTH` or `uuid` | User UUID | `5dc15e15-f285-4a9d-959b-0e4fbdd77b63` | `your-uuid` || `PROXYIP` or `proxyip` or `proxyIP` | Proxy server IP list | `13.230.34.30` | `tw.tp81.netlib.re` |

| `SUB_PATH` or `subpath` | Subscription path | `link` | `sub` |

| `DISABLE_TROJAN` or `CLOSE_TROJAN` | Whether to disable the Trojan protocol, true disables, false enables | `false` | Default enabled |

## Deployment Steps

1. **Log in to Cloudflare Dashboard**

- Access [Cloudflare Dashboard](https://dash.cloudflare.com/)

- Log in to your account

2. **Create a Worker**

- Click "Workers & Pages"

- Click "Create application"

- Select "Create Worker"

- Enter the Worker name (avoid keywords like vless, proxy, etc., default is recommended)

3. **Upload Code**

- Upload the code Copy the contents of the `_worker.js` file to the editor

- Click "Deploy" in the upper right corner

4. **Configure Environment Variables**

- In the Worker settings, find "Settings" → "Variables"

- Add the required environment variables and bind the custom domain

- Click "Save"

5. **Access Custom Domain**

- Enter your login password to access the homepage and view the relevant subscription links

## Advanced Usage of Snippets/Workers Paths

### Related Path Explanation

<img width="700" height="600" alt="image" src="https://github.com/user-attachments/assets/86b3dd1d-bbca-4786-9bb3-430bf6700024" />

| Type | Example | Explanation |

|------|------|------|

| **Default Path** | `/?ed=2560` | Uses the default `proxyip` set in the code |

| **Domain** `proxyip** | `/?ed=2560&proxyip=proxyip.domain.com` or `proxyip=proxyip.domain.com` | Uses `proxyip` in domain name format |

| **proxyip with port** | `/?ed=2560&proxyip=ip:port` or `/proxyip=ip:port` | Uses `proxyip` with port number |

| **SOCKS5** | `/?ed=2560&proxyip=socks://user:pass@host:port` or `/proxyip=socks://user:pass@host:port` | Uses global SOCKS5 outbound protocol header can be socks5 |

| **HTTP** | `/?ed=2560&proxyip=http://user:pass@host:port` or `/proxyip=http://user:pass@host:port` | Uses global HTTP/HTTPS outbound protocol |

## cloudns Bidirectional DNS resolution and snippet deployment: A unified domain prefix is ​​used for the following:

``bash

_acme-challenge

```

## Shadowsocks Node Parameter Comparison Chart

The node path starts with the SSpath variable or UUID. Example: `/5dc15e15-f285-4a9d-959b-0e4fbdd77b63/?ed=2560` Example with proxyip: `/5dc15e15-f285-4a9d-959b-0e4fbdd77b63/?ed=2560&proxyip=xxxx` You can remove `?ed=2560&` to customize the proxyip or enable global outbound DNS.

<img width="1585" height="1420" alt="PixPin_2025-11-20_21-30-22" src="https://github.com/user-attachments/assets/1ce9060f-9a0d-4093-99e3-4548ee7ac869" />

## License

GPL 2.0

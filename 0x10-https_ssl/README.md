HTTPS SSL 💻

In this project, I learned about the importance of HTTPS and how it works.
Tasks 📃

    0. World wide web
        1-world_wide_web: Bash script that displays information about subdomains on my configured servers.
        Usage: ./1-world_wide_web <domain> <subdomain>
        Output: The subdomain [SUB_DOMAIN] is a [RECORD_TYPE] record and points to [DESTINATION]
        If no subdomain parameter is passed, displays information about the subdomains www, lb-01, web-01 and web-02, in that order.

    1. HAproxy SSL termination
        2-haproxy_ssl_termination: HAproxy configuration file that accepts encrypted SSL traffic for the subdomain www. on TCP port 443.
        
  100.   A good habit is to enforce HTTPS traffic so that no unencrypted traffic is possible. Configure HAproxy to automatically redirect HTTP traffic to HTTPS.

Requirements:

    This should be transparent to the user
    HAproxy should return a 301
    HAproxy should redirect HTTP traffic to HTTPS
    Share your HAproxy config as an answer file (/etc/haproxy/haproxy.cfg)


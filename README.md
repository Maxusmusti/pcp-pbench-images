# pcp-pbench-images

Can be found on quay.io/meyceoz/pcp-collector and quay.io/meyceoz/pcp-exposer

Usage for collector:
`podman pull quay.io/meyceoz/pcp-collector`

`podman run --systemd always -v /<path>/<to>/<log_folder>/:/var/log/pcp/pmlogger:Z -v /<path>/<to>/<remotes>:/etc/pcp/pmlogger/control.d/remote:Z --network host quay.io/meyceoz/pcp-collector`
 - the log_folder can be any empty folder, and the entries in the remote file should look like this:
   - `<HOST> n n PCP_LOG_DIR/pmlogger/<HOST> -r -T24h10m -c config.<HOST>`
 - Remember to use absolute paths

Usage for exposer:
`podman pull quay.io/meyceoz/pcp-exposer`

`podman run --network host quay.io/meyceoz/pcp-exposer`
- Make sure port 44321 is accessible on the remote node, and is not currently in use before running

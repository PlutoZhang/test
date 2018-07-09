# Verifying zLUX installation

To verify the zLUX installation, you can open the MVD in any supported browser.

1. In a supported browser, open the MVD at `https://myhost:httpsPort/ZLUX/plugins/com.rs.mvd/web/index.html` where:
   * `myHost` is the host on which you ran the Giza Node server.
   * `httpPort` is the value that was assigned to `node.http.port` in `zluxserver.json`.
   * `httpsPort` is the value that was assigned to `node.https.port` in `zluxserver.json`.

     For example, if you ran the Giza Node server on host `myhost` and the value that is assigned to `node.http.port` in `zluxserver.json` is 12345, you would specify `https://myhost:12345/ZLUX/plugins/com.rs.mvd/web/index.htm`.
2. Browse the interface.


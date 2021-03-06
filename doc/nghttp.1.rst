
nghttp(1)
=========

SYNOPSIS
--------

**nghttp** [OPTIONS]... <URI>...

DESCRIPTION
-----------

HTTP/2 experimental client

.. describe:: <URI>

    Specify URI to access.

OPTIONS
-------

.. option:: -v, --verbose

    Print   debug   information   such  as   reception   and
    transmission of frames and name/value pairs.  Specifying
    this option multiple times increases verbosity.

.. option:: -n, --null-out

    Discard downloaded data.

.. option:: -O, --remote-name

    Save  download  data  in  the  current  directory.   The
    filename is  dereived from URI.   If URI ends  with '*/*',
    'index.html'  is used  as a  filename.  Not  implemented
    yet.

.. option:: -t, --timeout=<SEC>

    Timeout each request after <SEC> seconds.

.. option:: -w, --window-bits=<N>

    Sets the stream level initial window size to 2\*\*<N>-1.

.. option:: -W, --connection-window-bits=<N>

    Sets  the  connection  level   initial  window  size  to
    2\*\*<N>-1.

.. option:: -a, --get-assets

    Download assets  such as stylesheets, images  and script
    files linked  from the downloaded resource.   Only links
    whose  origins are  the same  with the  linking resource
    will be downloaded.   nghttp prioritizes resources using
    HTTP/2 dependency  based priority.  The  priority order,
    from highest to lowest,  is html itself, css, javascript
    and images.

.. option:: -s, --stat

    Print statistics.

.. option:: -H, --header=<HEADER>

    Add a header to the requests.  Example: :option:`-H`\':method: PUT'

.. option:: --trailer=<HEADER>

    Add a trailer header to the requests.  <HEADER> must not
    include pseudo header field  (header field name starting
    with ':').  To  send trailer, one must use  :option:`-d` option to
    send request body.  Example: :option:`--trailer` 'foo: bar'.

.. option:: --cert=<CERT>

    Use  the specified  client certificate  file.  The  file
    must be in PEM format.

.. option:: --key=<KEY>

    Use the  client private key  file.  The file must  be in
    PEM format.

.. option:: -d, --data=<FILE>

    Post FILE to server. If '-'  is given, data will be read
    from stdin.

.. option:: -m, --multiply=<N>

    Request each URI <N> times.  By default, same URI is not
    requested twice.  This option disables it too.

.. option:: -u, --upgrade

    Perform HTTP Upgrade for HTTP/2.  This option is ignored
    if the request URI has https scheme.  If :option:`-d` is used, the
    HTTP upgrade request is performed with OPTIONS method.

.. option:: -p, --weight=<WEIGHT>

    Sets priority group weight.  The valid value range is
    [1, 256], inclusive.

    Default: ``16``

.. option:: -M, --peer-max-concurrent-streams=<N>

    Use  <N>  as  SETTINGS_MAX_CONCURRENT_STREAMS  value  of
    remote endpoint as if it  is received in SETTINGS frame.
    The default is large enough as it is seen as unlimited.

.. option:: -c, --header-table-size=<SIZE>

    Specify decoder header table size.

.. option:: -b, --padding=<N>

    Add at  most <N>  bytes to a  frame payload  as padding.
    Specify 0 to disable padding.

.. option:: -r, --har=<FILE>

    Output HTTP  transactions <FILE> in HAR  format.  If '-'
    is given, data is written to stdout.

.. option:: --color

    Force colored log output.

.. option:: --continuation

    Send large header to test CONTINUATION.

.. option:: --no-content-length

    Don't send content-length header field.

.. option:: --no-dep

    Don't send dependency based priority hint to server.

.. option:: --dep-idle

    Use idle streams as anchor nodes to express priority.

.. option:: --version

    Display version information and exit.

.. option:: -h, --help

    Display this help and exit.


The <SIZE> argument is an integer and an optional unit (e.g., 10K is
10 * 1024).  Units are K, M and G (powers of 1024).

SEE ALSO
--------

:manpage:`nghttpd(1)`, :manpage:`nghttpx(1)`, :manpage:`h2load(1)`

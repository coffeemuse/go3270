Go 3270 Server Library
======================

[![PkgGoDev](https://pkg.go.dev/badge/github.com/racingmars/go3270)](https://pkg.go.dev/github.com/racingmars/go3270)

This library allows you to write Go servers for tn3270 clients by building 3270 data streams from fields and processing the client's response to receive the attention keys and field values entered by users.

**Project status:** This library has been used by a small number of projects, and I believe the overall functionality is sound and relatively bug-free. Feedback is appreciated. At this point, I will try not to make breaking changes to the API, but I have not yet declared the library to be at v1.0, so I make no promises.

Usage
-----

See the example folders for quick demonstrations of using the library:

 * example1 uses the lower-level function ShowScreenOpts().
 * example2 uses a higher-level convenience function HandleScreen().
 * example3 demonstrates updating the client's 3270 display while waiting for a response by using an update thread and a waiting response thread.
 * example4 demonstrates the RunTransactions() approach to handing control from one screen to the next. This is the recommended way to build applications using go3270.
 * example5 demonstrates support for larger-than-default (24x80) terminal sizes.

**NEW**: For larger applications, I recommend using the `RunTransactions()` function to serve as the driver for your application. You can implement transaction functions which pass control from one transaction to another. example4 demonstrates a "larger" application that uses this approach.

Here's [a video introducing the library][introVideo] as well.

[introVideo]: https://www.youtube.com/watch?v=h9XTjup5W5U

3270 information
----------------

I started learning about 3270 data streams from [Tommy Sprinkle's tutorial][sprinkle]. The tn3270 telnet negotiation is gleaned from [RFC 1576: TN3270 Current Practices][rfc1576], [RFC 1041: Telnet 3270 Regime Option][rfc1041], and [RFC 854: Telnet Protocol Specification][rfc854]. The IANA maintains a [useful reference of telnet option numbers][telnetOptions]. The reference I use for 3270 data streams is [the 1981 version from IBM][ibmref].

[sprinkle]: http://www.tommysprinkle.com/mvs/P3270/
[rfc1576]: https://tools.ietf.org/html/rfc1576
[rfc1041]: https://tools.ietf.org/html/rfc1041
[rfc854]: https://tools.ietf.org/html/rfc854
[telnetOptions]: https://www.iana.org/assignments/telnet-options/telnet-options.xhtml
[ibmref]: https://bitsavers.org/pdf/ibm/3270/GA23-0059-0_3270_Data_Stream_Programmers_Reference_Jan1981.pdf

License
-------

This library is licensed under the MIT license; see the file LICENSE for details.

nomatch mode - property replacer - rsyslog.con
==============================================

This is a part of the `rsyslog.conf documentation <rsyslog_conf.html>`_
of the `property replacer <property_replacer.html>`_.

**The "nomatch-Mode" specifies which string the property replacer shall
return if a regular expression did not find the search string.**.
Traditionally, the string "\*\*NO MATCH\*\*" was returned, but many
people complained this was almost never useful. Still, this mode is
support as "**DFLT**\ " for legacy configurations.

Three additional and potentially useful modes exist: in one (**BLANK**)
a blank string is returned. This is probably useful for inserting values
into databases where no value shall be inserted if the expression could
not be found.

A similar mode is "**ZERO**\ " where the string "0" is returned. This is
suitable for numerical values. A use case may be that you record a
traffic log based on firewall rules and the "bytes transmitted" counter
is extracted via a regular expression. If no "bytes transmitted" counter
is available in the current message, it is probably a good idea to
return an empty string, which the database layer can turn into a zero.

The other mode is "**FIELD**\ ", in which the complete field is
returned. This may be useful in cases where absense of a match is
considered a failure and the message that triggered it shall be logged.

If in doubt, **it is highly suggested to use the** `rsyslog online regular
expression checker and generator <http://www.rsyslog.com/tool-regex>`_
**to see these options in action**. With that online tool, you can craft
regular expressions based on samples and try out the different modes.

Summary of nomatch Modes
------------------------

+------------+-----------------------------------------------------------+
| **Mode**   | **Returned**                                              |
+------------+-----------------------------------------------------------+
| DFLT       | "\*\*NO MATCH\*\*"                                        |
+------------+-----------------------------------------------------------+
| BLANK      | "" (empty string)                                         |
+------------+-----------------------------------------------------------+
| ZERO       | "0"                                                       |
+------------+-----------------------------------------------------------+
| FIELD      | full content of original field                            |
+------------+-----------------------------------------------------------+
|            | `Interactive Tool <http://www.rsyslog.com/tool-regex>`_   |
+------------+-----------------------------------------------------------+

[`manual index <manual.html>`_\ ]
[`rsyslog.conf <rsyslog_conf.html>`_\ ] [`rsyslog
site <http://www.rsyslog.com/>`_\ ]

This documentation is part of the `rsyslog <http://www.rsyslog.com/>`_
project.
Copyright © 2008 by `Rainer Gerhards <http://www.gerhards.net/rainer>`_
and `Adiscon <http://www.adiscon.com/>`_. Released under the GNU GPL
version 2 or higher.

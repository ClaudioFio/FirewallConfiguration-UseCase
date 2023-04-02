WWW and WWW2 servers can be identified with a single ACL rule

The binary representation of the IP addresses of WWW and WW2 are respectively:
<br>
146.48.58.20 = 10010010.00110000.00111010.0001<span style="color:red">**0**</span>100 <br>
146.48.58.28 = 10010010.00110000.00111010.0001<span style="color:red">**1**</span>100 <br>

From this representation, it can be seen that the two ip addresses differ only by the bit highlighted in red, reasoning that it is sufficient to set the wildcard mask "0.0.0.8" in order to identify WWW and WWW2 with a single ACL rule.

0.0.0.8&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; -> 00000000.00000000.00000000.0000<span style="color:red">**1**</span>000  <br>
146.48.58.20  -> 10010010.00110000.00111010.0001<span style="color:green">**0**</span>100  <br>
146.48.58.28  -> 10010010.00110000.00111010.0001<span style="color:green">**1**</span>100 <br>

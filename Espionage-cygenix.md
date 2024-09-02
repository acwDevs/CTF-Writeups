
Challenge Description:
![[Pasted image 20240825174755.png]]

This one was quite simple we start with a pcap file so guess its time open up wireshark.

After some looking around I found some http request those are always nice so lets take a look.
We can set a filter in wirehark to only display http request.

This is the result of applying the filter
![[Pasted image 20240825182900.png]]

After some looking around in each of the captures I found a username and password inside a post request sent to /pages/main.html

![[Pasted image 20240825183351.png]]

The password looks like it might be encoded in some sort of format lets look through the other request to see if we can find the function that is used to encode the password.

After some looking I found in the first get response to /index.html there is a javascript function called modify pass. 
![[Pasted image 20240825183533.png]]

Now we can be sure the password is encoded in some sort of format. Lets lookup what btoa does and if we can reverse it.

Found this [link](https://www.w3schools.com/jsref/met_win_btoa.asp) that describes it btoa()
It just uses base64 to encode the passwd

base64 can be reversed lets find a website that can do it for us.

![[Pasted image 20240825183942.png]]


There we go we got the flag.

CyGenixCTF{PApdsjRTae}





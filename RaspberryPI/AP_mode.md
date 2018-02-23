라즈베리파이는 독립형 네트워크를 실행하는 무선 AP로 사용할 수 있습니다.

이것은 라즈베리파이3와 라즈베리파이제로W에 내장된 무선 기능을 사용하던가 아니면 AP를 지원하는 무선 USB동글을 사용함으로서 사용할 수 있습니다.

이 문서는 라즈베리파이3 에서 테스트 된 것과 몇몇의 USB동글에서는 약간 바뀌는 세팅이 있다는 것을 유념하세요. 만약 USB무선 동글을 사용하는데 문제가 있다면 포럼을 확인하세요.

라즈베리파이가 AP로 작동하기 위해서 AP소프트웨어를 설치할 필요가 있다, 연결된 장치들에게 네트워크 주소를 제공하는 DHCP 서버와 함께. 당신의 라즈베리 파이가 2017년 이후의 버전인지 확인을 하십시오.

한번에 필요한 소프트웨어를 전부 설치하세요
<pre>
<code>
sudo apt-get install dnsmasq hostapd
</code>
</pre>

설정 파일이 아직 준비되지 않았기 때문에, 다음 새 소프트웨어를 꺼줍니다.
<pre>
<code>
sudo systemctl stop dnsmasq
sudo systemctl stop hostapd
</code>
</pre>

### 정적(static) IP 설정

서버로 작동하도록 독립형 네트워크를 구성하므로 라즈베리파이에서는 정적 IP 주소가 무선 포트에 할당되어있어야 합니다. 이 설명서에서는 무선 네트워크에 표준 192.168.x.x IP 주소를 사용하고 있다고 가정하므로 서버에 IP 주소 192.168.4.1을 할당합니다. 이것은 또한 무선 장치가 wlan0을 사용하고 있다고 가정합니다.

정적 IP를 설정하기 위해 dhcpcd 설정 파일을 수정합니다 :
<pre>
<code>
sudo nano /etc/dhcpcd.conf
</code>
</pre>

파일의 끝에 가서 다음과 같이 수정합니다.
<pre>
<code>
interface wlan0
  static ip_address=192.168.4.1/24    
</code>
</pre>

이제 dhcpcd 데몬을 재시작하고 새로운 wlan0 설정을 셋업합니다 :
<pre>
<code>
sudo service dhcpcd restart
</code>
</pre>

### DHCP서버 설정(dnsmasq)
DHCP 서비스는 dnsmasq에 의해 제공됩니다. 기본적으로 설정 파일은 필요하지 않은 많은 정보들을 포함합니다 그러므로 처음부터 다시 시작하는 것이 쉽습니다. 이름을 다시 설정하고 새로운 것을 편집합니다 :
<pre>
<code>
sudo mv /etc/dnsmasq.conf /etc/dnsmasq.conf.orig  
sudo nano /etc/dnsmasq.conf
</code>
</pre>

다음 정보를 dnsmasq 설정 파일에 입력하거나 복사하여 저장하세요 :
<pre>
<code>
interface=wlan0      # Use the require wireless interface - usually wlan0
  dhcp-range=192.168.4.2,192.168.4.20,255.255.255.0,24h
</code>
</pre>

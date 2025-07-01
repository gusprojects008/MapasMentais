# Ataques a redes WPA/WPA2-Personal
- ## Pré requisitos
- ## KRAK (Key Reinstallation Attack)
  Uma fescoberto em 2017, que explora uma falha no
  handshake 4-Way, que permite que um reenvie (injete) o pacote EAPOL 3, 
  fazendo com que o dispositivo reutilize e reinstale a mesma PTK,
  e assim o contador de replay do pacote 3 irá resetar, 
  permitindo que o atacante injete ou retransmitir pacotes antigos, ou descriptografar parcialmente ou completamento o trafégo de rede.
  forçe um dispositivo
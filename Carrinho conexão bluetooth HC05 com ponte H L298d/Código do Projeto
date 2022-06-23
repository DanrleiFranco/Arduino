#include <SoftwareSerial.h>
//biblioteca com os pinos de comunicação do módulo bluetooth com o Arduino:
SoftwareSerial DADOS(10, 11);/* RX -> pino 11 , TX -> pino 10 */
//definição dos pinos:
#define in_1 3
#define in_2 5
#define in_3 6
#define in_4 9
#define led 13
#define buzzer 12

void setup(){
  // Habilitação dos pinos como saídas:
  pinMode(in_1, OUTPUT);
  pinMode(in_2, OUTPUT);
  pinMode(in_3, OUTPUT);
  pinMode(in_4, OUTPUT);
  pinMode(buzzer, OUTPUT);
  pinMode(led, OUTPUT);
  // mostra os sinais enviados no monitor serial: 
  Serial.begin(9600);
  DADOS.begin(9600);
}

void loop(){  

   byte velocidade = 250;
   //armazena os sinais recebidos pelo módulo bluetooth:
   char leitor_Sinal_Serial;
              
    if(DADOS.available()) {  
      leitor_Sinal_Serial = DADOS.read(); 
      Serial.println(leitor_Sinal_Serial);
    }
  
    switch(leitor_Sinal_Serial){

       // COMPONENTES EXTERNOS:
      case 'W':
        digitalWrite(led, HIGH); // LED dianteiro acesso
        break;
      case 'w':
        digitalWrite(led, LOW); // LED dianteiro apagado
        break;
      case 'V':
        digitalWrite(buzzer, HIGH);// BUZINA Ligada
        break;
      case 'v':
        digitalWrite(buzzer, LOW);// BUZINA Apagada
        break;
        
      // COMANDO DOS MOTORES:  
      case 'F':{
        //Serial.print("CIMA: ");
        digitalWrite(in_1, LOW);
        analogWrite(in_2, velocidade);
        digitalWrite(in_3, LOW);
        analogWrite(in_4, velocidade);
        break;
      }
      case 'B':{
        //Serial.print("BAIXO: ");
        analogWrite(in_1, velocidade);
        digitalWrite(in_2, LOW);
        analogWrite(in_3, velocidade);
        digitalWrite(in_4, LOW);
        break;
      }
      case 'R':{
        //Serial.print("DIREITA: ");
        analogWrite(in_1, velocidade);
        digitalWrite(in_2, LOW);
        digitalWrite(in_3, LOW);
        analogWrite(in_4, velocidade);
        break;
      }
      case 'L':{
        //Serial.print("ESQUERDA: ");
        digitalWrite(in_1, LOW);
        analogWrite(in_2, velocidade);
        analogWrite(in_3, velocidade);
        digitalWrite(in_4, LOW);
        break;
      }
      default :{
        // Serial.print("MOTORES DESLIGADOS:: ");
        digitalWrite(in_1, LOW);
        digitalWrite(in_2, LOW);
        digitalWrite(in_3, LOW);
        digitalWrite(in_4, LOW);
      }
    } 
  }

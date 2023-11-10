```c
#include "address.h"

//Function definitions

unsigned char UARTRx(void);
void UARTTx(unsigned char data);
void UARTTxString(char*pt);
void UARTRxString(char*bufPt, unsigned short max);
void UARTInit(void)

{

SYSCTL_RCGC_UART_R |= (1<<0)|(1<<1);
SYSCTL_RCGC_GPIO_R |= (1<<0)|(1<<3);

  
GPIO_PORTD_LOCK_R = 0x4C4F434B ;
GPIO_PORTA_CR_R |= (1<<7);
GPIO_PORTA_AFSEL_R |= 0x3;
GPIO_PORTA_PCTL_R |= 0x11;
GPIO_PORTD_AFSEL_R |= 0xc0;
GPIO_PORTD_PCTL_R |= 0x11000000;
  

UART0_CTL_R &= ~(0x1);
UART2_CTL_R &= ~(0x1);

UART0_IBRD_R=0x8;
UART2_IBRD_R=0x8;

//FBRD=int(0.6805*64+0.5)=44
UART0_IBRD_R=0x2c;
UART2_IBRD_R=0x2c;

UART0_LCRH_R = 0x50;
UART2_LCRH_R = 0x50;

UART0_CTL_R |= (1<<0)|(1<<8)|(1<<9);
UART2_CTL_R |= (1<<0)|(1<<8)|(1<<9);
}
//Wait for input and returns its ASCII value
unsigned char UARTRx(void)
{
	while((UART2_FR_R & 0x40)!=0);
	return((unsigned char)(UART2_DR_R & 0xFF));
}

void UARTRxString (char *pt, unsigned short max)
{
	int length=0;
	char character;
	for(int i; i < max; i++)
	{
		character = UARTRx();
		if (character >= 141)
		{
			character = character - 40;
		}

		else if (character <= 132)
		{
			character = character + 40;
		}
		
		*pt=character;
		pt++;
		length++;
	}
}

//Output 8bit to serial port
void UARTTx(unsigned char data)
{
	while((UART0_FR_R & 0x80)!=0);
	UART0_DR_R = data;
}

//Output a character string to serial port
void UARTTxString(char *pt)
{
	while(*pt)
	{
		UARTTx(*pt);
		pt++;
	}

}

int main(void)
{
	char string[17];
	UARTInit();

	while(1)
	{
		UARTRxString(string,16);
		UARTTxString(string);
	}

}
```

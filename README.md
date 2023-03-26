## Code for Printing "Hello" using I2C Protocol in CubeIDE

```
#include "main.h"
#include<string.h>                        // To add string libraries

// Create Constants
static const uint8_t pphl_ADDR = 0X48 <<1; // 7 bit addr is shifted to left by 1 bit to leave a space for R/W Bit as 8-Bit addr is used
static const uint8_t pphl_REG_ADDR = 0x00;
int main(void)
{
HAL_StatusTypeDef ret;                     //  Numeration that results in various return values store in ret
uint8_t buf[12];                           // Created a buffer of size 12 
int16_t val;                               // stores the data from pphl
while(1)
{ 
// Tell the pphl that we want to read from the pphl register
	  buf[0] = pphl_REG_ADDR;                 //set 1st byte of the buffer to the register of pphl
	  ret = HAL_I2C_Master_Transmit(&hi2c1, pphl_ADDR, buf, 1, HAL_MAX_DELAY);
	  if (ret != HAL_OK){
		  strcpy((char*)buf, "ERROR Tx\r\n");
	  }
	  else{

		  //Read bytes from the pphl
		  ret = HAL_I2C_Master_Receive(&hi2c1, pphl_ADDR, buf, 1, HAL_MAX_DELAY);
		  if (ret != HAL_OK){
		 		  strcpy((char*)buf, "ERROR Tx\r\n");
		  }
		  else{
			  val; // stores the data in val
		  }
	  }
strcpy((char*)buf,"Hello\r\n";             //Copies the character to the destination i.e. 'buffer' ; strcpy(dest,to be copied)
HAL_UART_Transmit(&huart1, buf, strlen((char*)buf, HAL_MAX_DELAY);  
HAL_Delay(500);                           // Prints after every 0.5 s
 }
}
```


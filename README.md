## Code for Printing "Hello" using I2C Protocol in CubeIDE

```
#include "main.h"
#include<string.h>                 // To add string libraries
int main(void)
{
uint8_t buf[12];                   // Created a buffer of size 12 
while(1)
{ 
strcpy((char*)buf,"Hello\r\n";     //Copies the character to the destination i.e. 'buffer' ; strcpy(dest,to be copied)
HAL_UART_Transmit(&huart1, buf, strlen((char*)buf, HAL_MAX_DELAY);  
HAL_Delay(500);                    // Prints after every 0.5 s
 }
}
```


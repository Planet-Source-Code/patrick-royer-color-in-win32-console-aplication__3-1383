<div align="center">

## color in win32 console aplication


</div>

### Description

This code put colors in win32 Console aplication.
 
### More Info
 
He doesn't take any paramaters...

I take functions in windows.h headers for put colors. The 3 functions is :

SetConsoleTextAttribute(cxHandle, Color);

//To choose the color

SetConsoleCursorPosition(cxHandle, cxCoord);

//to move the cursor

WriteConsole(cxHandle, Text, strl(Text),  &Result, NULL);

//to print the text

Take care do you have the handle of the window and call the function whit it.

(In the example : cxHandle)

He doesn't return anything...


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Patrick Royer](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/patrick-royer.md)
**Level**          |Beginner
**User Rating**    |5.0 (15 globes from 3 users)
**Compatibility**  |Microsoft Visual C\+\+
**Category**       |[Miscellaneous](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/miscellaneous__3-1.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/patrick-royer-color-in-win32-console-aplication__3-1383/archive/master.zip)

### API Declarations

```
#include <windows.h>
#include <iostream.h>
```


### Source Code

```
	/************************************************
	*The declaration for WORD; COORD; DWORD; HANDLE**
	************************************************/
#include <windows.h>
	/***************************************************
	*The declaration for cout; FOREGROUND_; BACKGROUND_*
	***************************************************/
#include <iostream.h>
	/************************************************
	*  The declaration of an objet HANDLE  *
	************************************************/
HANDLE cxHandle;
	/******************************************************************
	*It's the function to Set posX, posY, the color And Print the Text*
	******************************************************************/
void SetPosXYAndColor(int x, int y, LPSTR Text, WORD Color);
	/************************************************
	*   Macro colors of Text    *
	************************************************/
#define BLUE FOREGROUND_BLUE
#define LIGHTBLUE FOREGROUND_BLUE | FOREGROUND_INTENSITY
#define RED FOREGROUND_RED
#define LIGHTRED FOREGROUND_RED | FOREGROUND_INTENSITY
#define GREEN FOREGROUND_GREEN
#define LIGHTGREEN FOREGROUND_GREEN | FOREGROUND_INTENSITY
#define PURPLE FOREGROUND_BLUE | FOREGROUND_RED
#define LIGHTPURPLE PURPLE | FOREGROUND_INTENSITY
#define BLUEGREEN FOREGROUND_BLUE | FOREGROUND_GREEN
#define LIGHTBLUEGREEN BLUEGREEN | FOREGROUND_INTENSITY
#define ORANGE FOREGROUND_GREEN | FOREGROUND_RED
#define YELLOW ORANGE | FOREGROUND_INTENSITY
#define INTENSITY FOREGROUND_INTENSITY
	/************************************************
	*  Macro colors for background   *
	************************************************/
#define BBLUE BACKGROUND_BLUE
#define BLIGHTBLUE BACKGROUND_BLUE | BACKGROUND_INTENSITY
#define BRED BACKGROUND_RED
#define BLIGHTRED BACKGROUND_RED | BACKGROUND_INTENSITY
#define BGREEN BACKGROUND_GREEN
#define BLIGHTGREEN BACKGROUND_GREEN | BACKGROUND_INTENSITY
#define BPURPLE BACKGROUND_BLUE | BACKGROUND_RED
#define BLIGHTPURPLE BPURPLE | BACKGROUND_INTENSITY
#define BBLUEGREEN BACKGROUND_BLUE | BACKGROUND_GREEN
#define BLIGHTBLUEGREEN BBLUEGREEN | BACKGROUND_INTENSITY
#define BORANGE BACKGROUND_GREEN | BACKGROUND_RED
#define BYELLOW ORANGE | BACKGROUND_INTENSITY
#define BINTENSITY BACKGROUND_INTENSITY
void main()
{
		/************************************************
		* cxHandle Take the HANDLE of the win32 Console *
		************************************************/
	cxHandle = GetStdHandle (STD_OUTPUT_HANDLE);
		/****************************************************
		*Call the function to setup the posX, posY, color *
		*And print the message...       *
		*****************************************************/
	SetPosXYAndColor(5,5, "Hello World!", YELLOW);
}
/******************************************************************
*It's the function to Set posX, posY, the color And Print the Text*
******************************************************************/
void SetPosXYAndColor(int x, int y, LPSTR Text, WORD Color)
{
		/************************************************************
		*  Declaration of an objet to take the return value  *
		************************************************************/
	DWORD Result;
		/************************************************************
		*Declaration of an objet to take the posX and posY of cursor*
		************************************************************/
	COORD cxCoord;
	cxCoord.X = x;
	cxCoord.Y = y;
		/**************************************************
		* Setup the color on the screen by the HANDLE *
		**************************************************/
	SetConsoleTextAttribute(cxHandle, Color);
		/*****************************************************
		*Setup the CursorPosition on the screen by the HANDLE*
		*****************************************************/
	SetConsoleCursorPosition(cxHandle, cxCoord);
		/************************************************************
		*  Write the text on the screen whit previous settings *
		************************************************************/
	WriteConsole(cxHandle, Text, strlen(Text), &Result, NULL);
}
```


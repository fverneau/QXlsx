# QXlsx Examples

## HelloWorld
- Hello world example

```cpp
// [0] include QXlsx headers 
#include "xlsxdocument.h"
#include "xlsxchartsheet.h"
#include "xlsxcellrange.h"
#include "xlsxchart.h"
#include "xlsxrichstring.h"
#include "xlsxworkbook.h"
using namespace QXlsx;

int main(int argc, char *argv[])
{
	QCoreApplication app(argc, argv);

	// [1]  Writing excel file(*.xlsx)
    QXlsx::Document xlsxW;
    xlsxW.write("A1", "Hello Qt!"); // write "Hello Qt!" to cell(A,1). it's shared string.
    xlsxW.saveAs("Test.xlsx"); // save the document as 'Test.xlsx'

	// [2] Reading excel file(*.xlsx)
    Document xlsxR("Test.xlsx"); // load excel file
    if (xlsxR.isLoadPackage())
	{ 
		int row = 1; int col = 1;
        Cell* cell = xlsxR.cellAt(row, col); // get cell pointer.
        if ( cell != NULL )
        {
            QVariant var = cell->readValue(); // read cell value (number(double), QDateTime, QString ...)
            qDebug() << var; // display value
        }
	}
 
	return 0;
}
```

## TestExcel
- Basic samples based on QtXlsx samples

## HelloAndroid : Android Example
- See 'HelloAndroid' example using QML and native C++.
- Qt 5.11.1 / QtCreator 4.6.2 / gcc 4.9 / Android x86 (using Emulator [Android Oreo]) / Android Studio 3.1.3 (Android NDK 17.1)

![](markdown.data/android.jpg)

## Copycat : Windows Widget Example
- Load xlsx file and display on Qt widgets. 
- Print xlsx to papaer. (TODO: save xlsx)

![](markdown.data/copycat.png)

## WebServer : WebServer Example
- Load xlsx file and display on Web.
- Connect to http://127.0.0.1:3001

![](markdown.data/webserver.png)
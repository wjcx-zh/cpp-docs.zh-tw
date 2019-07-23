---
title: 輸入資料流成員函式
ms.date: 07/19/2019
helpviewer_keywords:
- input stream objects
- input streams, member functions
ms.assetid: b4b9465d-0da9-4ccf-859d-72a68418982e
ms.openlocfilehash: 3b028090c9b91c7f0dde195243a5d2daef55fbbc
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2019
ms.locfileid: "68376242"
---
# <a name="input-stream-member-functions"></a>輸入資料流成員函式

輸入資料流成員函式是用於磁碟輸入。

## <a name="vclrftheopenfunctionforinputstreamsanchor11"></a>斷開

如果您使用輸入檔資料流程 (`ifstream`), 您必須將該資料流程與特定的磁片檔案產生關聯。 您可以在此函式中執行此動作, 也可以`open`使用函數。 不論是上述哪一種情況，引數都相同。

當您開啟與輸入資料流程相關聯的檔案時, 通常會指定[ios_base:: openmode](../standard-library/ios-base-class.md#openmode)旗標 (預設模式`ios::in`為)。 如需`openmode`旗標的清單, 請參閱[ios_base:: openmode](../standard-library/ios-base-class.md#openmode)。 這些旗標可以與位元 OR ( &#124; ) 運算子合併使用。

若要讀取檔案, 請先使用`fail`成員函式來判斷它是否存在:

```cpp
istream ifile("FILENAME");

if (ifile.fail())
// The file does not exist ...
```

## <a name="vclrfthegetfunctionanchor12"></a>獲取

未格式化`get`的成員`>>`函式的運作方式類似運算子, 但有兩個例外狀況。 首先, `get`函式包含空白字元, 而`skipws`當設定旗標 (預設值) 時, 此功能會排除空白字元。 第二, `get`函式較不可能造成系結的輸出資料流程`cout`(例如) 排清。

函式的變化`get`會指定緩衝區位址, 以及要讀取的最大字元數。 這對於限制傳送給特定變數的字元數來說，相當有用，如以下範例所示：

```cpp
// ioo_get_function.cpp
// compile with: /EHsc
// Type up to 24 characters and a terminating character.
// Any remaining characters can be extracted later.
#include <iostream>
using namespace std;

int main()
{
   char line[25];
   cout << " Type a line terminated by carriage return\n>";
   cin.get( line, 25 );
   cout << line << endl;
}
```

### <a name="input"></a>輸入

```Input
1234
```

### <a name="sample-output"></a>範例輸出

```Output
1234
```

## <a name="vclrfthegetlinefunctionanchor13"></a>getline

此`getline`成員函式類似`get`于函式。 這兩個函式都允許使用第三引數來指定輸入的終止字元。 預設值是新行字元。 這兩個函式都會保留一個字元作為所需的終止字元。 不過, `get`會將終止字元保留在資料流程中`getline` , 並移除終止字元。

以下範例會指定輸入資料流的終止字元：

```cpp
// getline_func.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char line[100];
   cout << " Type a line terminated by 't'" << endl;
   cin.getline( line, 100, 't' );
   cout << line;
}
```

### <a name="input"></a>輸入

```Input
test
```

## <a name="vclrfthereadfunctionanchor14"></a>閱讀文章

`read`成員函式會將位元組從檔案讀取到指定的記憶體區域。 長度引數會決定所讀取的位元組數目。 如果您未將該引數包含在內，則在到達檔案的實際結尾時就會停止讀取，或在文字模式檔案的案例中，則是會在讀取到內嵌的 `EOF` 字元時停止讀取。

此範例會從薪資檔案將二進位記錄讀取到結構中：

```cpp
#include <fstream>
#include <iostream>
using namespace std;

int main()
{
   struct
   {
      double salary;
      char name[23];
   } employee;

   ifstream is( "payroll" );
   if( is ) {  // ios::operator void*()
      is.read( (char *) &employee, sizeof( employee ) );
      cout << employee.name << ' ' << employee.salary << endl;
   }
   else {
      cout << "ERROR: Cannot open file 'payroll'." << endl;
   }
}
```

此程式假設資料記錄的格式完全如結構所指定, 而不含終止的回車或換行字元。

## <a name="vclrftheseekgandtellgfunctionsanchor7"></a>seekg 和 tellg

輸入檔案資料流會保留內部指標，該指標指向檔案中接下來要讀取資料的位置。 您可以使用 `seekg` 函式來設定這個指標，如下所示：

```cpp
#include <iostream>
#include <fstream>
using namespace std;

int main( )
{
   char ch;

   ifstream tfile( "payroll" );
   if( tfile ) {
      tfile.seekg( 8 );        // Seek 8 bytes in (past salary)
      while ( tfile.good() ) { // EOF or failure stops the reading
         tfile.get( ch );
         if( !ch ) break;      // quit on null
         cout << ch;
      }
   }
   else {
      cout << "ERROR: Cannot open file 'payroll'." << endl;
   }
}
```

若要`seekg`使用來執行記錄導向的資料管理系統, 請將固定長度記錄大小乘以記錄數目, 以取得相對於檔案結尾的位元組位置, 然後`get`使用物件來讀取記錄。

`tellg` 成員函式會傳回目前的檔案位置以供讀取。 此值的類型為 `streampos`，這是在 \<iostream> 中定義的 `typedef`。 以下範例會讀取檔案，並顯示指出空格位置的訊息。

```cpp
#include <fstream>
#include <iostream>
using namespace std;

int main( )
{
   char ch;
   ifstream tfile( "payroll" );
   if( tfile ) {
       while ( tfile.good( ) ) {
          streampos here = tfile.tellg();
          tfile.get( ch );
          if ( ch == ' ' )
             cout << "\nPosition " << here << " is a space";
       }
   }
   else {
      cout << "ERROR: Cannot open file 'payroll'." << endl;
   }
}
```

## <a name="vclrftheclosefunctionforinputstreamsanchor15"></a>關閉

`close`成員函式會關閉與輸入檔資料流程相關聯的磁片檔案, 並釋出作業系統檔案控制代碼。 此[`ifstream`](../standard-library/basic-ifstream-class.md)析構函式會為您關閉檔案, 但如果您`close`需要為相同的資料流程物件開啟另一個檔案, 則可以使用函數。

## <a name="see-also"></a>另請參閱

[輸入資料流](../standard-library/input-streams.md)<br/>

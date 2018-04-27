---
title: 輸入資料流成員函式 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- input stream objects
- input streams, member functions
ms.assetid: b4b9465d-0da9-4ccf-859d-72a68418982e
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 791ea1d8e994bf6795f28dfc16032673337dd8db
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="input-stream-member-functions"></a>輸入資料流成員函式

輸入資料流成員函式是用於磁碟輸入。 成員函式包括：

- [輸入資料流的 open 函式](#vclrftheopenfunctionforinputstreamsanchor11)

- [Get](#vclrfthegetfunctionanchor12)

- [Getline](#vclrfthegetlinefunctionanchor13)

- [唯讀](#vclrfthereadfunctionanchor14)

- [seekg 和 tellg 函式](#vclrftheseekgandtellgfunctionsanchor7)

- [輸入資料流的 close 函式](#vclrftheclosefunctionforinputstreamsanchor15)

## <a name="vclrftheopenfunctionforinputstreamsanchor11"></a> 輸入資料流的 open 函式

如果您使用輸入檔案資料流 (ifstream)，就必須將該資料流與特定的磁碟檔案建立關聯。 您可以在建構函式中進行此操作，或是使用 **open** 函式。 不論是上述哪一種情況，引數都相同。

當您開啟與輸入資料流關聯的檔案時，通常需指定 [ios_base::openmode](../standard-library/ios-base-class.md#openmode) 旗標 (預設模式為 **ios::in**)。 取得一份**open_mode**旗標，請參閱[開啟](#vclrftheopenfunctionforinputstreamsanchor11)。 這些旗標可以與位元 OR ( &#124; ) 運算子合併使用。

若要讀取檔案，請先使用 **fail** 成員函式來判斷它是否存在：

```cpp
istream ifile("FILENAME");

if (ifile.fail())
// The file does not exist ...
```

## <a name="vclrfthegetfunctionanchor12"></a> Get

未格式化的 **get** 成員函式運作方式與 **>>** 運算子相同，但有兩個例外。 第一，**get** 函式包含空白字元，但在已設定 **skipws** 旗標 (預設) 的情況下，擷取器則會排除空白字元。 第二，**get** 函式較不可能導致將繫結的輸出資料流 (例如 `cout`) 清除。

**get** 函式的變化可指定緩衝區位址，以及要讀取的字元數上限。 這對於限制傳送給特定變數的字元數來說，相當有用，如以下範例所示：

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

## <a name="vclrfthegetlinefunctionanchor13"></a> Getline

**getline** 成員函式與 **get** 函式類似。 這兩個函式都允許使用第三引數來指定輸入的終止字元。 預設值是新行字元。 這兩個函式都會保留一個字元作為所需的終止字元。 不過，**get** 會保留資料流中的終止字元，而 **getline** 則是會移除終止字元。

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

## <a name="vclrfthereadfunctionanchor14"></a> 唯讀

**read** 成員函式會從檔案將位元組讀取到指定的記憶體區域。 長度引數會決定所讀取的位元組數目。 如果您未將該引數包含在內，則在到達檔案的實際結尾時就會停止讀取，或在文字模式檔案的案例中，則是會在讀取到內嵌的 `EOF` 字元時停止讀取。

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

程式會假設資料記錄是完全依照結構指定的方式格式化，沒有任何終止歸位字元或換行字元。

## <a name="vclrftheseekgandtellgfunctionsanchor7"></a> seekg 和 tellg 函式

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

若要使用 `seekg` 來實作記錄導向資料管理系統，請將固定長度記錄大小乘以記錄數目，以取得相對於檔案結尾的位元組位置，然後使用 **get** 物件來讀取記錄。

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

## <a name="vclrftheclosefunctionforinputstreamsanchor15"></a> 輸入資料流的 close 函式

**close** 成員函式會關閉與輸入檔案資料流關聯的磁碟檔案，然後釋出作業系統控制代碼。 [ifstream](../standard-library/basic-ifstream-class.md) 解構函式會為您關閉檔案，但如果您需要為相同的資料流物件開啟另一個檔案，則可以使用 **close** 函式。

## <a name="see-also"></a>另請參閱

[輸入資料流](../standard-library/input-streams.md)<br/>

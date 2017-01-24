---
title: "輸入資料流成員函式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "輸入資料流物件"
  - "輸入資料流, 成員函式"
ms.assetid: b4b9465d-0da9-4ccf-859d-72a68418982e
caps.latest.revision: 7
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 輸入資料流成員函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

輸入資料流的成員函式鍵盤輸入使用。  成員函式包括:  
  
-   [輸入資料流的開啟函式](#vclrftheopenfunctionforinputstreamsanchor11)  
  
-   [取得函式](#vclrfthegetfunctionanchor12)  
  
-   [getline 函式](#vclrfthegetlinefunctionanchor13)  
  
-   [讀取的函式](#vclrfthereadfunctionanchor14)  
  
-   [seekg 和 tellg 函式](#vclrftheseekgandtellgfunctionsanchor7)  
  
-   [輸入資料流的存取函式](#vclrftheclosefunctionforinputstreamsanchor15)  
  
##  <a name="vclrftheopenfunctionforinputstreamsanchor11"></a> 輸入資料流的開啟函式  
 如果您使用的輸入檔案資料流 \(ifstream\)，您必須與該資料流與特定磁碟檔案。  您可以在建構函式，也可以使用 **open** 函式。  在任何情況下，引數是相同的。  
  
 您通常會指定 [ios\_base::openmode](../Topic/ios_base::openmode.md) 旗標，則當您開啟檔案與輸入資料流時 \(預設模式是 **ios::in**\)。  如需 **open\_mode** 旗標的清單，請參閱 [開啟函式](#vclrftheopenfunctionforinputstreamsanchor11)。  旗標可以結合位元 OR \(&#124;\) 運算子。  
  
 若要讀取檔案，請先使用 **fail** 成員函式來判斷它是否存在:  
  
```  
istream ifile( "FILENAME" );  
if ( ifile.fail() )  
// The file does not exist ...  
```  
  
##  <a name="vclrfthegetfunctionanchor12"></a> 取得函式  
 未格式化的 **get** 成員函式的運作方式與 **\>\>** 運算子有兩個例外狀況。  首先， **get** 函式包含空白字元，反之，擷取器排除泛空白字元，當 [skipws](../Topic/skipws.md) 旗標設為 \(預設值\)。  其次， **get** 函式不太可能導致繫結的輸出資料流 \(例如`cout`\)，清除。  
  
 **get** 函式的變化指定緩衝區位址和最大字元數讀取。  因為這個範例顯示，這會限制字元數是有用的傳送到特定變數:  
  
```  
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
  
### 輸入  
  
```  
1234  
```  
  
### 範例輸出  
  
```  
1234  
```  
  
##  <a name="vclrfthegetlinefunctionanchor13"></a> getline 函式  
 **getline** 成員函式類似 **get** 函式。  兩個函式允許為項目指定結束字元第三個引數。  預設值是新行字元。  兩個函式為必要的結尾字元保留一個字元。  不過， **get** 資料流的結尾字元保留，並取消 **getline** 結尾的字元。  
  
 下列範例指定輸入資料流指定的終止字元:  
  
```  
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
  
### 輸入  
  
```  
test  
```  
  
##  <a name="vclrfthereadfunctionanchor14"></a> 讀取的函式  
 **read** 成員函式從檔案讀取位元組至記憶體中的指定區域。  引數的長度判斷所讀取的位元組數目。  如果您未包含該引數，將停止文字模式檔案的情況下，，當實體檔案結尾為止，或者，，當內嵌 `EOF` 字元讀取時。  
  
 這個範例會將一個二進位資料錄從薪資檔案的結構:  
  
```  
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
  
 程式會假設，資料錄正確地格式化依結構沒有終止歸位字元或換行字元。  
  
##  <a name="vclrftheseekgandtellgfunctionsanchor7"></a> seekg 和 tellg 函式  
 輸入檔案資料流保留內部指標至資料是要讀取的下一個檔案的位置。  將與 `seekg` 的這個函式指標，如下所示:  
  
```  
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
  
 若要使用 `seekg` 實作記錄導向資料管理系統，請將固定長度記錄大小以記錄編號取得位元組相對於檔案結尾，然後使用 **get** 物件讀取資料錄。  
  
 `tellg` 成員函式來傳回讀取目前的檔案位置。  iostream\>屬於型別 `streampos`， `typedef` 定義的這 \<個值。  下列範例會讀取檔案並顯示空間的位置的訊息。  
  
```  
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
  
##  <a name="vclrftheclosefunctionforinputstreamsanchor15"></a> 輸入資料流的存取函式  
 **close** 成員函式關閉磁碟檔與輸入檔資料流並釋放作業系統檔案控制代碼。  [ifstream](../standard-library/basic-ifstream-class.md) 解構函式關閉您的檔案，不過，您可以使用 **close** 函式需要開啟相同物件的另一個檔案。  
  
## 請參閱  
 [輸入資料流](../standard-library/input-streams.md)
---
title: "輸出檔資料流成員函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "輸出資料流, 成員函式"
ms.assetid: 38aaf710-8035-4a34-a0c4-123a5327f28a
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 輸出檔資料流成員函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

輸出資料流成員函式有三種類型:與操作相同執行未格式化的寫入作業的項目，否則修改資料流狀態並沒有對等的操作工具或插入運算子的以及。  對於循序，格式化輸出，您可能只使用插入運算子和操作工具。  對於隨機存取二進位磁碟輸出，您使用其他成員函式，不論是否有插入運算子。  
  
## 輸出資料流的開啟函式  
 若要使用輸出檔案資料流 \([ofstream](../Topic/ofstream.md)\)，您必須與該資料流與建構函式或 **open** 函式的特定磁碟檔案。  如果您使用 **open** 函式，您可以重複使用於一系列檔案的相同物件。  在任何情況下，描述檔案的引數是相同的。  
  
 當您開啟檔案與輸出資料流時，通常會指定 **open\_mode** 旗標。  您可以結合這些旗標，定義為 `ios` 類別的列舉程式，使用位元 OR \(&#124;\) 運算子。  提供列舉程式清單參閱 [ios\_base::openmode](../Topic/ios_base::openmode.md) 。  
  
 三種常見的輸出資料流的情況包括模式選項:  
  
-   建立檔案。  如果檔案已經存在，舊版刪除。  
  
    ```  
    ostream ofile( "FILENAME" );  // Default is ios::out  
    ofstream ofile( "FILENAME", ios::out ); // Equivalent to above  
    ```  
  
-   將記錄附加至現有檔案或建立，如果它不存在。  
  
    ```  
    ofstream ofile( "FILENAME", ios::app );  
    ```  
  
-   開啟兩個檔案，一次一個，在相同。  
  
    ```  
    ofstream ofile();  
    ofile.open( "FILE1", ios::in );  
    // Do some output  
    ofile.close(); // FILE1 closed  
    ofile.open( "FILE2", ios::in );  
    // Do some more output  
    ofile.close(); // FILE2 closed  
    // When ofile goes out of scope it is destroyed.  
    ```  
  
## put 函式  
 **put** 函式寫入輸出資料流中的字元。  預設為下列兩個陳述式是相同的，不過，第二個是 Managed 資料流的格式引數的影響:  
  
```  
cout.put( 'A' ); // Exactly one character written  
cout << 'A'; // Format arguments 'width' and 'fill' apply   
```  
  
## 寫入函式  
 **write** 函式給輸出檔案資料流寫入記憶體區塊。  引數的長度指定寫入的位元組數目。  這個範例會建立輸出檔案資料流並在其中寫入 `Date` 結構的二進位值:  
  
```  
// write_function.cpp  
// compile with: /EHsc  
#include <fstream>  
using namespace std;  
  
struct Date  
{  
   int mo, da, yr;  
};  
  
int main( )  
{  
   Date dt = { 6, 10, 92 };  
   ofstream tfile( "date.dat" , ios::binary );  
   tfile.write( (char *) &dt, sizeof dt );  
}  
```  
  
 **write** 函式不會停止，並在到達 null 字元，因此，完整類別結構寫入。  函式會採用兩個引數: `char` 指標和寫入的字元計數。  請注意所需的轉換至 **char\*** ，結構物件的位址。  
  
## seekp 和 tellp 函式  
 輸出檔案資料流保留指向位置資料會寫入下的內部指標。  `seekp` 成員函式會將這個指標而提供隨機存取磁碟檔案輸出。  `tellp` 成員函式來傳回檔案位置。  如需使用輸入資料流相當於 `seekp` 和 `tellp`的範例，請參閱 [seekg 和 tellg 函式](../standard-library/input-stream-member-functions.md)。  
  
## 輸出資料流的存取函式  
 **close** 成員函式關閉磁碟檔案與輸出檔案資料流。  必須關閉檔案完成所有磁碟輸出。  如果需要 `ofstream` ，解構函式關閉您的檔案，不過，您可以使用 **close** 函式需要開啟相同物件的另一個檔案。  
  
 在建構函式或 **open** 成員函式開啟的檔案時，輸出資料流的解構函式自動關閉資料流的檔案。  如果您透過建構函式已開啟檔案的檔案描述項或使用 **attach** 成員函式，您必須明確地關閉檔案。  
  
##  <a name="vclrferrorprocessingfunctionsanchor10"></a> 處理函式的錯誤。  
 請使用這些成員函式來測試錯誤，在寫入至資料流時:  
  
|功能|傳回值|  
|--------|---------|  
|[終結](../Topic/basic_ios::bad.md)|如果有一個無法復原的錯誤，傳回 **true** 。|  
|[失敗](../Topic/basic_ios::fail.md)|傳回 **true** ，如果有一個無法復原的錯誤或一個「必須有」情形，例如轉譯錯誤，或者，如果找不到檔案。  處理可能在呼叫之後通常復原至具有零的引數 **clear** 。|  
|[好](../Topic/basic_ios::good.md)|傳回 **true** ，如果沒有錯誤條件 \(無法復原或\)，且檔案結尾旗標未設定。|  
|[eof](../Topic/basic_ios::eof.md)|傳回這個文件關閉條件的 **true** 。|  
|[clear](../Topic/basic_ios::clear.md)|設定內部錯誤狀態。  如果呼叫具有預設引數，它會清除所有錯誤位元。|  
|[rdstate](../Topic/basic_ios::rdstate.md)|傳回目前錯誤狀態。|  
  
 **\!** 運算子多載執行和 **fail** 函式相同。  因此運算式:  
  
```  
if( !cout)...  
```  
  
 等於：  
  
```  
if( cout.fail() )...  
```  
  
 **void\*\(\)** 運算子多載是 **\!** 運算子相反;因此運算式:  
  
```  
if( cout)...  
```  
  
 等於:  
  
```  
if( !cout.fail() )...  
```  
  
 因為它不會測試檔案結尾， **void\*\(\)** 和 **good** 運算子不相等。  
  
## 請參閱  
 [輸出資料流](../standard-library/output-streams.md)
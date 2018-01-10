---
title: "輸出檔資料流成員函式 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: output streams [C++], member functions
ms.assetid: 38aaf710-8035-4a34-a0c4-123a5327f28a
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 25313cce5d032c4c3975fffbf8ca89b232031661
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="output-file-stream-member-functions"></a>輸出檔資料流成員函式
輸出資料流的成員函式有三種類型：相當於操作工具的類型、會執行未格式化寫入作業的類型，以及其他會修改資料流狀態，且沒有對等的操作工具或插入運算子的類型。 對於循序的格式化輸出，您可能僅會使用插入運算子和操作工具。 對於隨機存取二進位磁碟輸出，您會使用其他的成員函式 (無論搭配插入運算子與否)。  
  
## <a name="the-open-function-for-output-streams"></a>輸出資料流的 open 函式  
 若要使用輸出檔案資料流 ([ofstream](../standard-library/basic-ofstream-class.md))，您必須在建構函式或是 **open** 函式中，將該資料流與特定的磁碟檔案建立關聯。 如果您使用 **open** 函式，您就可以重複使用相同的資料流物件搭配一系列檔案。 不論使用哪一種，描述檔案的引數都一樣。  
  
 當您開啟與輸出資料流相關聯的檔案時，通常會指定 **open_mode** 旗標。 您可以使用位元 OR ( &#124; ) 運算子，來合併這些在 `ios` 類別中定義為列舉程式的旗標。 如需列舉程式的清單，請參閱 [ios_base::openmode](../standard-library/ios-base-class.md#openmode)。  
  
 有三種常見的輸出資料流情況會牽涉到模式選項：  
  
-   建立檔案。 如果檔案已經存在，將會刪除舊版本檔案。  
  
 ```  
    ostream ofile("FILENAME");
// Default is ios::out  
    ofstream ofile("FILENAME", ios::out);

// Equivalent to above  
```  
  
-   將記錄附加到現有檔案，或在檔案不存在的情況下建立檔案。  
  
 ```  
    ofstream ofile("FILENAME", ios::app);
```  
  
-   在相同的資料流上開啟兩個檔案，一次開啟一個。  
  
 ```  
    ofstream ofile();
ofile.open("FILE1",
    ios::in);
// Do some output  
    ofile.close();

// FILE1 closed  
    ofile.open("FILE2",
    ios::in);
// Do some more output  
    ofile.close();

// FILE2 closed  // When ofile goes out of scope it is destroyed.  
```  
  
## <a name="the-put"></a>Put
 **put** 函式會將一個字元寫入輸出資料流。 下列兩個陳述式的預設值都相同，但第二個會受到資料流的格式引數影響：  
  
```  
cout.put('A');

// Exactly one character written  
cout <<'A'; // Format arguments 'width' and 'fill' apply   
```  
  
## <a name="the-write"></a>寫入
 **write** 函式會寫入輸出檔案資料流的記憶體區塊。 長度引數會指定要寫入的位元組數目。 這個範例會建立輸出檔案資料流，並將 `Date` 結構的二進位值寫入它：  
  
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
  
 **write** 函式遇到 null 字元時並不會停止，因此會寫入完整的類別結構。 此函式會採用兩個引數：`char` 指標和要寫入的字元計數。 請注意，在結構物件的位址之前必須轉型成 **char\***。  
  
## <a name="the-seekp-and-tellp-functions"></a>seekp 和 tellp 函式  
 輸出檔案資料流會保留內部指標，該指標指向接下來要寫入資料的位置。 `seekp` 成員函式會設定此指標，並提供隨機存取磁碟檔案輸出。 `tellp` 成員函式會傳回檔案位置。 如需使用對應至 `seekp` 和 `tellp` 的輸入資料流範例，請參閱 [seekg 和 tellg 函式](../standard-library/input-stream-member-functions.md)。  
  
## <a name="the-close-function-for-output-streams"></a>輸出資料流的 close 函式  
 **close** 成員函式會關閉與輸出檔案資料流相關聯的磁碟檔案。 若要完成所有的磁碟輸出，必須先關閉檔案。 如有必要，`ofstream` 解構函式能為您關閉檔案，但如果您需要在相同的資料流物件中開啟另一個檔案，您可以使用 **close** 函式。  
  
 輸出資料流解構函式只有在建構函式或是 **open** 成員函式開啟檔案後，才會自動關閉資料流的檔案。 如果您將已開啟之檔案的檔案描述元傳遞給建構函式，或使用 **attach** 成員函式，您必須明確地關閉檔案。  
  
##  <a name="vclrferrorprocessingfunctionsanchor10"></a> 錯誤處理函式  
 寫入資料流時，請使用下列成員函式來測試是否發生錯誤：  
  
|功能|傳回值|  
|--------------|------------------|  
|[bad](http://msdn.microsoft.com/Library/4038d331-e9c9-48b0-bf49-c6505744469c)|如果有無法復原的錯誤，則傳回 **true**。|  
|[fail](http://msdn.microsoft.com/Library/619f1b36-1e72-4551-8b48-888ae4e370d2)|如果有無法復原的錯誤，或是「預期」的狀況 (例如轉換錯誤，或是找不到檔案)，則傳回 **true**。 在呼叫不具有引數的 **clear** 之後，通常可以繼續處理。|  
|[good](http://msdn.microsoft.com/Library/77f0aa17-2ae1-48ae-8040-592d301e3972)|如果沒有任何錯誤狀況 (無論是否可復原) 且未設定檔案結尾旗標，則會傳回 **true**。|  
|[eof](http://msdn.microsoft.com/Library/3087f631-1268-49cd-86cf-ff4108862329)|針對檔案結尾條件傳回 **true**。|  
|[clear](http://msdn.microsoft.com/Library/dc172694-1267-45f8-8f5c-e822e16fc271)|設定內部錯誤狀態。 如果使用預設引數呼叫，它會清除所有錯誤位元。|  
|[rdstate](http://msdn.microsoft.com/Library/e235e4e2-7e95-4777-a160-3938d263dd9c)|傳回目前的錯誤狀態。|  
  
 **!** 運算子會多載以執行與 **fail** 函式相同的功能。 因此運算式︰  
  
```  
if(!cout)...  
```  
  
 等於：  
  
```  
if(cout.fail())...  
```  
  
 **void\*()** 運算子會多載成為相反的 **!** 運算子；因此運算式：  
  
```  
if(cout)...  
```  
  
 等於：  
  
```  
if(!cout.fail())...  
```  
  
 **void\*()** 運算子不等於 **good**，因為它並不會測試檔案結尾。  
  
## <a name="see-also"></a>請參閱  
 [輸出資料流](../standard-library/output-streams.md)


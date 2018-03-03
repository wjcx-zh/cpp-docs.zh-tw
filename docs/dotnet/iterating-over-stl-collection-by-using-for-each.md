---
title: "使用每個反覆查看 c + + 標準程式庫集合 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- DTL collections, iterating over
ms.assetid: 9358ca29-b982-4a19-bbfd-bef50fe66c9a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1a4ce2de13380895f1f313559abeb87e4cd65db2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="iterating-over-c-standard-library-collection-by-using-for-each"></a>使用每個反覆查看 c + + 標準程式庫集合
`for each`關鍵字可以用來反覆查看 c + + 標準程式庫集合。  
  
## <a name="all-platforms"></a>所有平台  
 **備註**  
  
 C + + 標準程式庫集合就是所謂*容器*。 如需詳細資訊，請參閱 [C++ 標準程式庫容器](../standard-library/stl-containers.md)。  
  
## <a name="examples"></a>範例  
 **範例**  
  
 下列程式碼範例使用`for each`來反覆查看[\<對應 >](../standard-library/map.md)。  
  
```  
// for_each_stl.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
#include <string>  
using namespace std;  
  
int main() {  
   int retval  = 0;  
   map<string, int> months;  
  
   months["january"] = 31;  
   months["february"] = 28;  
   months["march"] = 31;  
   months["april"] = 30;  
   months["may"] = 31;  
   months["june"] = 30;  
   months["july"] = 31;  
   months["august"] = 31;  
   months["september"] = 30;  
   months["october"] = 31;  
   months["november"] = 30;  
   months["december"] = 31;  
  
   map<string, int> months_30;  
  
   for each( pair<string, int> c in months )  
      if ( c.second == 30 )  
         months_30[c.first] = c.second;  
  
   for each( pair<string, int> c in months_30 )  
      retval++;  
  
   cout << "Months with 30 days = " << retval << endl;  
}  
```  
  
 **輸出**  
  
```Output  
Months with 30 days = 4  
```  
  
 **範例**  
  
 下列程式碼範例會使用 const 的參考 (`const&`) 與 c + + 標準程式庫容器的反覆項目變數。 您可以使用參考 (`&`) 為反覆項目上的變數可以宣告為任何的類型集合*T*`&`。  
  
```  
// for_each_stl_2.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
using namespace std;  
  
int main() {  
   int retval = 0;  
  
   vector<int> col(3);  
   col[0] = 10;  
   col[1] = 20;  
   col[2] = 30;  
  
   for each( const int& c in col )  
      retval += c;  
  
   cout << "retval: " << retval << endl;  
}  
```  
  
 **輸出**  
  
```Output  
retval: 60  
```  
  
## <a name="windows-runtime"></a>Windows 執行階段  
 **備註**  
  
 沒有平台特定備註有關這項功能。  
  
### <a name="requirements"></a>需求  
 編譯器選項： **/ZW**  
  
## <a name="common-language-runtime"></a>Common Language Runtime 
 **備註**  
  
 沒有平台特定備註有關這項功能。  
  
### <a name="requirements"></a>需求  
 編譯器選項： **/clr**  
  
## <a name="see-also"></a>請參閱  
 [針對每個，在](../dotnet/for-each-in.md)   
 [執行階段平台的元件延伸模組](../windows/component-extensions-for-runtime-platforms.md)
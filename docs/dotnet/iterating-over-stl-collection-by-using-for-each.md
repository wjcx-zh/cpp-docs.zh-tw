---
title: "使用 for each 反覆查看 STL 集合 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DTL 集合, 反覆"
ms.assetid: 9358ca29-b982-4a19-bbfd-bef50fe66c9a
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# 使用 for each 反覆查看 STL 集合
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`for each` 關鍵字可用來逐一查看在 Standard C\+\+ 程式庫 \(STL\) 集合。  
  
## 所有平台  
 **備註**  
  
 也稱為 STL 集合是 *容器*。  如需詳細資訊，請參閱[STL 容器](../standard-library/stl-containers.md)。  
  
## 範例  
 **範例**  
  
 下列程式碼範例會使用 `for each` 逐一查看 [\< 對應 \>](../standard-library/map.md)。  
  
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
  
 **Output**  
  
  **與 30 天的月份 \= 4** **範例**  
  
 下列程式碼範例為與 STL 容器的反覆運算變數使用常數參考 \(`const&`\)。  您可以使用參考 \(`&`\) 做為可宣告為 *T*`&`型別的所有集合的反覆運算變數。  
  
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
  
 **Output**  
  
  **retval: 60**   
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 **備註**  
  
 沒有這項功能的平台特定備註。  
  
### 需求  
 編譯器選項：**\/ZW**  
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 **備註**  
  
 沒有這項功能的平台特定備註。  
  
### 需求  
 編譯器選項：**\/clr**  
  
## 請參閱  
 [for each、in](../dotnet/for-each-in.md)   
 [Component Extensions for Runtime Platforms](../windows/component-extensions-for-runtime-platforms.md)
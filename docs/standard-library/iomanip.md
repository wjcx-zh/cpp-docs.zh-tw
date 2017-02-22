---
title: "&lt; &gt; iomanip | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "iomanip/std::<iomanip>"
  - "std::<iomanip>"
  - "<iomanip>"
  - "std.<iomanip>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "iomanip 標頭"
ms.assetid: 3681c346-4763-4037-bba4-cf0dc3447974
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# &lt; &gt; iomanip
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包含 `iostreams` 標準標頭 `<iomanip>` 來定義數個操作工具，每個接受單一引數。  
  
## 語法  
  
```  
  
#include <iomanip>  
  
```  
  
## 備註  
 其中每個操作工具會傳回一個未指定的類型，稱為 **T1** 至 **T10**，同時多載 `basic_istream`\<**Elem**, **Tr**\>`::`[operator\>\>](../Topic/operator%3E%3E%20\(%3Cistream%3E\).md) 和 `basic_ostream`\<**Elem**, **Tr**\>`::`[operator\<\<](../Topic/operator%3C%3C%20\(%3Costream%3E\).md)。  
  
### 操作工具  
  
|||  
|-|-|  
|[get\_money](../Topic/%3Ciomanip%3E%20get_money.md)|取得貨幣金額，可選用國際格式。|  
|[get\_time](../Topic/%3Ciomanip%3E%20get_time.md)|使用指定的格式來取得時間結構的時間。|  
|[put\_money](../Topic/%3Ciomanip%3E%20put_money.md)|提供貨幣金額，可選用國際格式。|  
|[put\_time](../Topic/%3Ciomanip%3E%20put_time.md)|以時間結構和要使用的格式字串來提供時間。|  
|[用引號括住](../Topic/quoted.md)|可使用插入和擷取運算子以方便往返字串。|  
|[resetiosflags](../Topic/resetiosflags.md)|清除指定的旗標。|  
|[setbase](../Topic/setbase.md)|設定整數的基底。|  
|[setfill](../Topic/setfill.md)|設定將用來填滿靠右對齊顯示中的空格字元。|  
|[setiosflags](../Topic/setiosflags.md)|設定指定的旗標。|  
|[setprecision](../Topic/setprecision.md)|設定浮點值的有效位數。|  
|[setw](../Topic/setw.md)|指定顯示欄位的寬度。|  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [iostreams 慣例](../standard-library/iostreams-conventions.md)
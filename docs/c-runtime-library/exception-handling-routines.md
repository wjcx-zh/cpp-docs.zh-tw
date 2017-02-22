---
title: "例外狀況處理常式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.exceptions"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "例外狀況處理, 常式"
ms.assetid: f60548c6-850a-4e1e-a79b-a2a6a541ab62
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 例外狀況處理常式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用 C\+\+ 例外狀況處理函式從執行期間的未預期的事件繼續程式。  
  
### 例外狀況處理函式  
  
|功能|用法|.NET Framework 對等用法|  
|--------|--------|-------------------------|  
|[\_set\_se\_translator](../c-runtime-library/reference/set-se-translator.md)|控制代碼 Win32 例外狀況 \(C\# 結構化例外狀況\) 做為 C\+\+ 語言的例外狀況|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[set\_terminate](../c-runtime-library/reference/set-terminate-crt.md)|安裝您自己的終止程序以被 `terminate`呼叫|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[set\_unexpected](../c-runtime-library/reference/set-unexpected-crt.md)|使用 `unexpected` 安裝終止函式|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[terminate](../c-runtime-library/reference/terminate-crt.md)|在特定情況下在例外狀況擲回後自動呼叫。  `terminate` 函式會呼叫 `abort` 或使用 `set_terminate`指定您指定的函數|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[unexpected](../c-runtime-library/reference/unexpected-crt.md)|呼叫 `terminate` 或使用 `set_unexpected` 指定的您的函式。  目前 Microsoft C\+\+ 不會使用 `unexpected` 函式實做例外處理常式|[\<caps:sentence id\="tgt30" sentenceid\="ec8332f3bf55c7bd183338eca87744ec" class\="tgtSentence"\>System::Exception 類別\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.exception.aspx)|  
  
## 請參閱  
 [依分類區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)
---
title: "runtime_checks | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc-pragma.runtime_checks"
  - "runtime_checks_CPP"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "runtime_checks Pragma"
  - "Pragma, runtime_checks"
ms.assetid: ae50b43f-f88d-47ad-a2db-3389e9e7df5b
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# runtime_checks
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

停用或還原 [\/RTC](../build/reference/rtc-run-time-error-checks.md) 設定。  
  
## 語法  
  
```  
  
#pragma runtime_checks(  
"[runtime_checks]", {restore | off} )  
```  
  
## 備註  
 您無法啟用未使用編譯器選項啟用的執行階段檢查。 例如，如果您未指定 \/RTC，則指定 `#pragma runtime_checks( "s", restore)` 不會啟用堆疊框架驗證。  
  
 **runtime\_checks** pragma 必須出現在函式之外，並在出現該 pragma 後定義的第一個函式生效。**restore** 和 **off** 引數可開啟或關閉在 *runtime\_checks* 中指定的選項。  
  
 *runtime\_checks* 可以是下表所示的零個或多個參數。  
  
### runtime\_checks Pragma 的參數  
  
|參數|執行階段檢查的類型|  
|--------|---------------|  
|**秒**|啟用堆疊 \(框架\) 驗證。|  
|**C**|將值指派給會造成資料損失的較小資料類型時回報。|  
|**u**|變數在定義之前即使用時回報。|  
  
 這些是與搭配 \/RTC 編譯器選項使用的相同字母。 例如：  
  
```  
#pragma runtime_checks( "sc", restore )  
```  
  
 使用 **runtime\_checks** pragma 搭配空字串 \(**""**\) 是一種特殊形式的指示詞：  
  
-   當您使用 **off** 參數時，會將上表中所列的執行階段錯誤檢查關閉。  
  
-   當您使用 **restore** 參數時，會將執行階段錯誤檢查重設為您使用 \/RTC 編譯器選項指定的內容。  
  
```  
#pragma runtime_checks( "", off )  
.  
.  
.  
#pragma runtime_checks( "", restore )   
```  
  
## 請參閱  
 [Pragma 指示詞和 \_\_Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
 [RTC sample](http://msdn.microsoft.com/zh-tw/b3415b09-f6fd-43dc-8c02-9a910bc2574e)
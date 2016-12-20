---
title: "optimize | Microsoft Docs"
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
  - "vc-pragma.optimize"
  - "optimize_CPP"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "optimize pragma"
  - "Pragma, optimize"
ms.assetid: cb13c1cc-186a-45bc-bee7-95a8de7381cc
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# optimize
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定要依照函式逐一執行的最佳化。  
  
## 語法  
  
```  
  
#pragma optimize( "[optimization-list]", {on | off} )  
```  
  
## 備註  
 **optimize** pragma 必須出現在函式之外，並在出現該 pragma 後定義的第一個函式生效。  **on** 和 **off** 引數可開啟或關閉在 *optimization\-list* 中指定的選項。  
  
 *optimization\-list* 可以是下表所示的零個或多個參數。  
  
### 最佳化 Pragma 的參數  
  
|參數|最佳化類型|  
|--------|-----------|  
|**g**|啟用全域最佳化。|  
|**s** 或 **t**|指定機器碼的短 \(short\) 序列或快速 \(fast\) 序列。|  
|**y**|在程式堆疊上產生框架指標。|  
  
 這些是與搭配 [\/O](../build/reference/o-options-optimize-code.md) 編譯器選項使用的相同字母。  例如，下列 pragma 相當於 **\/Os** 編譯器選項：  
  
```  
#pragma optimize( "ts", on )  
```  
  
 使用 **optimize** pragma 搭配空字串 \(**""**\) 是一種特殊的指示詞格式：  
  
 當您使用 **off** 參數時，會將列在本主題前述表格中的最佳化關閉。  
  
 當您使用 **on** 參數時，就會將最佳化重設為您以 [\/O](../build/reference/o-options-optimize-code.md) 編譯器選項指定的最佳化。  
  
```  
#pragma optimize( "", off )  
.  
.  
.  
#pragma optimize( "", on )   
```  
  
## 請參閱  
 [Pragma 指示詞和 \_\_Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
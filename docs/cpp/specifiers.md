---
title: "規範 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "宣告規範"
  - "宣告, 規範"
  - "規範, 宣告中的"
ms.assetid: 8b14e844-9880-4571-8779-28c8efe44633
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 規範
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主題將描述 [宣告](../misc/declarations.md)的 *decl\-specifiers* \(宣告規範\) 元件。  
  
 下列預留位置和語言關鍵字為宣告指定名稱：  
  
 *storage\-class\-specifier*  
  
 *type\-specifier*  
  
 *function\-specifier*  
  
 [friend](../cpp/friend-cpp.md)  
  
 [typedef](http://msdn.microsoft.com/zh-tw/cc96cf26-ba93-4179-951e-695d1f5fdcf1)  
  
 [\_\_declspec](../cpp/declspec.md) `(` *extended\-decl\-modifier\-seq* `)`  
  
## 備註  
 宣告的 *decl\-specifiers* 部分是用來表示類型名稱時可接受的最長 *decl\-specifiers* 序列，但不包括指標或參考修飾詞。  宣告的其餘部分為 *declarator*，包括引入的名稱。  
  
 下表列出四個宣告，然後分別列出每個宣告的 *decl\-specifers* 和 *declarator* 元件。  
  
|宣告|*decl\-specifiers*|`declarator`|  
|--------|------------------------|------------------|  
|`char *lpszAppName;`|`char`|`*lpszAppName`|  
|`typedef char * LPSTR;`|`char`|`*LPSTR`|  
|`const int func1();`|`const int`|`func1`|  
|`volatile void *pvvObj;`|`volatile void`|`*pvvObj`|  
  
 由於 `signed`、`unsigned`、`long` 和 `short` 全都表示 `int`，因此接在其中一個關鍵字後面的 `typedef` 名稱會視為 *declarator\-list* 的成員，而不是 *decl\-specifiers* 的成員。  
  
> [!NOTE]
>  由於名稱可以重新宣告，因此其解譯會受到目前範圍中最新的宣告所限制。  重新宣告可能會影響編譯器解譯名稱的方式，尤其是 `typedef` 名稱。  
  
## 請參閱  
 [宣告](../misc/declarations.md)
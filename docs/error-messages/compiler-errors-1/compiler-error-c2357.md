---
title: "編譯器錯誤 C2357 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2357"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2357"
ms.assetid: d1083945-0ea2-4385-9e66-8c665978806c
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2357
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 必須是型別 'type' 的函式  
  
 您的程式碼所宣告的 `atexit` 函式版本與編譯器內部宣告的版本不相符。  請以下列方式來宣告 `atexit`：  
  
```  
int __cdecl atexit(void (__cdecl *)());  
```  
  
 如需詳細資訊，請參閱 [init\_seg](../../preprocessor/init-seg.md)。  
  
 下列範例會產生 C2357：  
  
```  
// C2357.cpp  
// compile with: /c  
// C2357 expected  
#pragma warning(disable : 4075)  
// Uncomment the following line to resolve.  
// int __cdecl myexit(void (__cdecl *)());  
#pragma init_seg(".mine$m",myexit)  
```
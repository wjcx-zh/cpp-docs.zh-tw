---
title: "編譯器警告 (層級 1) C4926 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4926"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4926"
ms.assetid: 5717fce0-146f-4ef2-bde0-e9a01c0922d1
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4926
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier': 已定義符號：忽略屬性  
  
 找到向前宣告，但具有相同名稱的屬性化結構已存在。 向前宣告的屬性會被忽略。  
  
 下列範例會產生 C4926：  
  
```  
// C4926.cpp // compile with: /W1 [module(name="MyLib")]; [coclass] struct a { }; [coclass] struct a;   // C4926 int main() { }  
```
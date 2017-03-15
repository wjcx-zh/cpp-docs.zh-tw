---
title: "編譯器錯誤 C3675 | Microsoft Docs"
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
  - "C3675"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3675"
ms.assetid: 87461613-6633-430b-b95d-c7cb1bb63776
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3675
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : 已被保留，因為 'property' 已經定義了  
  
 宣告簡單函式時，編譯器會產生 get 和 set 存取子方法，但這些名稱已出現在您程式的範圍中。編譯器產生的名稱是以在屬性名稱之前加上 get\_ 和 set\_ 的方式組成。因此，您不能用與編譯器所產生存取子相同的名稱宣告函式。  
  
 如需詳細資訊，請參閱[property](../../windows/property-cpp-component-extensions.md)。  
  
## 範例  
 下列範例會產生 C3675。  
  
```  
// C3675.cpp  
// compile with: /clr /c  
ref struct C {  
public:  
   property int Size;  
   int get_Size() { return 0; }   // C3675  
};  
```
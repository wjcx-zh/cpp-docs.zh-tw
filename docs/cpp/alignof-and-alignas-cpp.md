---
title: "alignof 和 alignas (C++) | Microsoft Docs"
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
ms.assetid: 1d18aa8a-9621-4fb5-86e5-4cc86d5187f4
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# alignof 和 alignas (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`alignas` 類型規範是可攜性的 C\+\+ 標準方式，用來指定變數和使用者定義類型的自訂對齊方式。  `alignof` 運算子同樣是標準的可攜性方式，用來取得指定類型或變數的對齊方式。  
  
## 範例  
 您可以對類別、結構或等位，或個別成員使用 `alignas`。  當遇到多個 `alignas` 規範時，編譯器會選擇最嚴格的一個 \(具有最大值者\)。  
  
```  
struct alignas(16) Bar  
{      
    int i;       // 4 bytes  
    int n;      // 4 bytes  
    alignas(4) char arr[3];  
    short s;          // 2 bytes  
};  
…  
cout << alignof(Bar) << endl; // output: 16  
  
```  
  
## 請參閱  
 [對齊方式](../cpp/alignment-cpp-declarations.md)
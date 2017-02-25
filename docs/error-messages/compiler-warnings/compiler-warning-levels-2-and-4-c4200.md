---
title: "編譯器警告 (層級s 2 and 4) C4200 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4200"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4200"
ms.assetid: e44d6073-937f-42b7-acc1-65e802b475c6
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 編譯器警告 (層級s 2 and 4) C4200
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用非標準擴充：結構\/等位中大小為零的陣列  
  
 表示結構或等位包含大小為零的陣列。  
  
 宣告大小為零的陣列為 Microsoft 擴充功能。  這會導致編譯 C\+\+ 檔案時出現層級 2 警告以及編譯 C 檔案時出現層級 4 警告。  C \+ \+ 編譯也會發出這項警告：「UDT 包含大小為零的陣列時，無法產生 copy\-ctor 或 copy\-assignment 運算子」。本範例會產生警告 C4200：  
  
```cpp  
// C4200.cpp  
// compile by using: cl /W4 c4200.cpp  
struct A {  
    int a[0];  // C4200  
};  
int main() {  
}  
```  
  
 這個非標準擴充功能經常用於具有可變長度的外部資料結構的介面程式碼。  如果這種情況適用於您的程式碼，您可以停用這項警告：  
  
## 範例  
  
```cpp  
// C4200b.cpp  
// compile by using: cl /W4 c4200a.cpp  
#pragma warning(disable : 4200)  
struct A {  
    int a[0];  
};  
int main() {  
}  
```
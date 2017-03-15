---
title: "編譯器錯誤 C2774 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2774"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2774"
ms.assetid: 10f428c6-7f49-489a-92ba-6ef978b7caaf
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 編譯器錯誤 C2774
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 沒有與此屬性產生關聯的 'put' 方法  
  
 使用 [property](../../cpp/property-cpp.md) 宣告的資料成員不具有 `put` 函式，但有一個運算式嘗試設定其值。  
  
 下列範例會產生 C2774：  
  
```  
// C2774.cpp  
struct A {  
   __declspec(property(get=GetProp)) int prop;  
   int GetProp(void);  
  
   __declspec(property(get=GetProp2, put=PutProp2)) int prop2;  
   int GetProp2(void);  
   void PutProp2(int);  
};  
  
int main() {  
   A* pa = new A;  
   int val = 0;  
   pa->prop = val;   // C2774  
   pa->prop++;   // C2774  
}  
```
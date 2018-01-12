---
title: "編譯器錯誤 C2775 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2775
dev_langs: C++
helpviewer_keywords: C2775
ms.assetid: 9c488508-ade0-48f1-b94f-d538d15f807a
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 77462b90a0e24084426a8186912631cf6a323cb9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2775"></a>編譯器錯誤 C2775
'identifier': 不 'get' 方法，這個屬性與相關聯  
  
 資料成員宣告與[屬性](../../cpp/property-cpp.md)延伸的屬性並沒有`get`函式指定，但運算式嘗試擷取其值。  
  
 下列範例會產生 C2775:  
  
```  
// C2775.cpp  
struct A {  
   __declspec(property(put=PutProp2, get=GetProp2)) int prop2;  
   int GetProp2(){return 0;}  
   void PutProp2(int){}  
  
   __declspec(property(put=PutProp)) int prop;  
   int PutProp(void){}  
  
};  
  
int main() {  
   A* pa = new A;  
   int x;  
   x = pa->prop;   // C2775  
   x = pa->prop2;  
}  
```
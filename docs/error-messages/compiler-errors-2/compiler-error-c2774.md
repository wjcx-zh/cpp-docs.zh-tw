---
title: 編譯器錯誤 C2774 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2774
dev_langs:
- C++
helpviewer_keywords:
- C2774
ms.assetid: 10f428c6-7f49-489a-92ba-6ef978b7caaf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0a6fc100bf7cd4a57c5c23630b28c41d92cf43d6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33234950"
---
# <a name="compiler-error-c2774"></a>編譯器錯誤 C2774
'identifier': 不 'put' 方法，這個屬性與相關聯  
  
 資料成員宣告與[屬性](../../cpp/property-cpp.md)之中未包含任何`put`函式，但運算式嘗試將其值設定。  
  
 下列範例會產生 C2774:  
  
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
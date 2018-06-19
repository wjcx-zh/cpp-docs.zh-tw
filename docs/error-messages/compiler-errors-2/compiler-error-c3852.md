---
title: 編譯器錯誤 C3852 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3852
dev_langs:
- C++
helpviewer_keywords:
- C3852
ms.assetid: 194e5c5e-0dfb-414e-86db-791c11eb610c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 439e6518c1e1f94918671f2e710ccf1a86621f16
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33272262"
---
# <a name="compiler-error-c3852"></a>編譯器錯誤 C3852
'member' 具有類型 'type': 彙總初始化無法初始化這個成員  
  
 嘗試彙總初始化過程中將無法在彙總初始化期間接收預設初始化的資料成員的預設初始化。  
  
 下列範例會產生 C3852:  
  
```  
// C3852.cpp  
struct S  
{  
   short s;  
};  
  
struct S1  
{  
   int i;  
   const S s;  
};  
  
struct S2  
{  
   int i;  
   char & rc;  
};  
  
int main()  
{  
   S1 s1 = { 1 };   // C3852 const member   
   // try the following line instead  
   // S1 s1 = { 1, 2 };  
  
   S2 s2 = { 2 };   // C3852 reference member  
   // try the following line instead  
   // char c = 'a';  
   S2 s2 = { 2, c };  
}  
```
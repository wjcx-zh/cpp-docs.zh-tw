---
title: "編譯器錯誤 C3286 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3286
dev_langs: C++
helpviewer_keywords: C3286
ms.assetid: 554328c8-cf44-4f7d-a8d2-def74d28ecdd
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ea704fce0aebd3ffa83410104b38ceb5d359a6c6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3286"></a>編譯器錯誤 C3286  
  
> '*規範*': 反覆運算變數不能有任何儲存類別規範  
  
儲存類別不能指定反覆項目變數。 如需詳細資訊，請參閱[儲存類別 （c + +）](../../cpp/storage-classes-cpp.md)和[針對每個，在](../../dotnet/for-each-in.md)。  
  
## <a name="example"></a>範例  
  
下列範例會產生 c3286:，，以及正確使用方式。  
  
```cpp  
// C3286.cpp  
// compile with: /clr  
int main() {  
   array<int> ^p = { 1, 2, 3 };  
   for each (static int i in p) {}   // C3286   
   for each (int j in p) {}   // OK  
}  
```
---
title: 編譯器錯誤 C2883 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2883
dev_langs:
- C++
helpviewer_keywords:
- C2883
ms.assetid: 5c6d689d-ed42-41ad-b5c0-e9c2e0b8c356
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc3119db27127521f5078a5753bb82c82da381ed
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33244943"
---
# <a name="compiler-error-c2883"></a>編譯器錯誤 C2883
'name': 由 using 宣告引入 'identifier' 函式宣告衝突  
  
 您嘗試一次以上定義的函式。 第一個定義已命名空間，與從`using`宣告。 第二個是區域定義。  
  
 下列範例會產生 C2883:  
  
```  
// C2883.cpp  
namespace A {  
   void z(int);  
}  
  
int main() {  
   using A::z;  
   void z(int);   // C2883  z is already defined  
}  
```
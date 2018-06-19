---
title: 編譯器錯誤 C3072 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3072
dev_langs:
- C++
helpviewer_keywords:
- C3072
ms.assetid: cdd5cb6b-c478-4698-adfa-c40188d34a18
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6287ba8e84df96adb0447728dbde8f2031c986cf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33252480"
---
# <a name="compiler-error-c3072"></a>編譯器錯誤 C3072
運算子 'operator' 無法套用至 ref 類別的執行個體  
  
 使用一元 '`operator` ' 運算子，將 ref 類別的執行個體轉換成控制代碼類型  
  
 CLR 型別需要 CLR 運算子，not 原生 （或標準） 的運算子。  如需詳細資訊，請參閱[追蹤參考運算子](../../windows/tracking-reference-operator-cpp-component-extensions.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3072。  
  
```  
// C3072.cpp  
// compile with: /clr  
ref class R {};  
  
int main() {  
   R r1;  
   R^ r2 = &r1;   // C3072  
   R^ r3 = %r1;   // OK  
}  
```
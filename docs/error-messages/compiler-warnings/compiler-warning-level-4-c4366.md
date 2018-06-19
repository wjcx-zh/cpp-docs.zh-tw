---
title: 編譯器警告 （層級 4） C4366 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4366
dev_langs:
- C++
helpviewer_keywords:
- C4366
ms.assetid: 65d2942f-3741-42f4-adf2-4920d5a055ca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 12410a567cb55d6dea74b8e5e595009e56b1071f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293698"
---
# <a name="compiler-warning-level-4-c4366"></a>編譯器警告 (層級 4) C4366
一元 'operator' 運算子的結果可能未對齊  
  
 如果因為封裝結構成員無法曾有未配置，編譯器會發出警告時成員的位址會指派給對齊的指標。 根據預設，所有指標都對齊。  
  
 若要解決 C4366，請變更結構的對齊方式或宣告指標[__unaligned](../../cpp/unaligned.md)關鍵字。  
  
 如需詳細資訊，請參閱 __unaligned 和[套件](../../preprocessor/pack.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4366。  
  
```  
// C4366.cpp  
// compile with: /W4 /c  
// processor: IPF x64  
#pragma pack(1)  
struct X {  
   short s1;  
   int s2;  
};  
  
int main() {  
   X x;  
   short * ps1 = &x.s1;   // OK  
   int * ps2 = &x.s2;   // C4366  
}  
```
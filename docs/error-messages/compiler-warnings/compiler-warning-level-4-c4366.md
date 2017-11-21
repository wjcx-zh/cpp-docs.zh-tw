---
title: "編譯器警告 （層級 4） C4366 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4366
dev_langs: C++
helpviewer_keywords: C4366
ms.assetid: 65d2942f-3741-42f4-adf2-4920d5a055ca
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0d610bfcf2e432870fc081298d3dfc3a60c73bd4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
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
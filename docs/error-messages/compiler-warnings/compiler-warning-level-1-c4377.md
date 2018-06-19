---
title: 編譯器警告 （層級 1） C4377 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4377
dev_langs:
- C++
helpviewer_keywords:
- C4377
ms.assetid: a1c797b8-cd5e-4a56-b430-d07932e811cf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ef049f85cd17bfeaba243b84da9fca93ae4036b0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33274777"
---
# <a name="compiler-warning-level-1-c4377"></a>編譯器警告 (層級 1) C4377
原生型別為私用的預設值;-d1PrivateNativeTypes 已被取代  
  
 在舊版中，組件中的原生型別是公用的預設值，而且內部且未記載的編譯器選項 (**/d1PrivateNativeTypes**) 用來使其私用。  
  
 所有類型，原生和 CLR，現在是私用預設會在組件，因此 **/d1PrivateNativeTypes**不再需要。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4377。  
  
```  
// C4377.cpp  
// compile with: /clr /d1PrivateNativeTypes /W1  
// C4377 warning expected  
int main() {}  
```
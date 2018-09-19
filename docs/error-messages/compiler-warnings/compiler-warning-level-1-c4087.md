---
title: 編譯器警告 （層級 1） C4087 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4087
dev_langs:
- C++
helpviewer_keywords:
- C4087
ms.assetid: 546e4d57-5c8e-422c-8ef1-92657336dad5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4be252163d9c45d2404629bcf9e2d82e3225a84a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086287"
---
# <a name="compiler-warning-level-1-c4087"></a>編譯器警告 (層級 1) C4087

'function' : 搭配 'void' 參數清單宣告

函式宣告沒有型式參數，但函式呼叫有實際的參數。 根據函式的呼叫慣例，傳遞了額外的參數。

這項警告是對於 C 編譯器。

## <a name="example"></a>範例

```
// C4087.c
// compile with: /W1
int f1( void ) {
}

int main() {
   f1( 10 );   // C4087
}
```
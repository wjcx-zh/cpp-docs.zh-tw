---
title: 編譯器警告 (層級 1) C4087
ms.date: 11/04/2016
f1_keywords:
- C4087
helpviewer_keywords:
- C4087
ms.assetid: 546e4d57-5c8e-422c-8ef1-92657336dad5
ms.openlocfilehash: fe2b4fadfb87726e81178a3530299dbb8620aec9
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626835"
---
# <a name="compiler-warning-level-1-c4087"></a>編譯器警告 (層級 1) C4087

'function' : 搭配 'void' 參數清單宣告

函式宣告沒有型式參數，但函式呼叫有實際的參數。 根據函式的呼叫慣例，傳遞了額外的參數。

這項警告是對於 C 編譯器。

## <a name="example"></a>範例

```c
// C4087.c
// compile with: /W1
int f1( void ) {
}

int main() {
   f1( 10 );   // C4087
}
```
---
title: 編譯器警告 （層級 1） C4028 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4028
dev_langs:
- C++
helpviewer_keywords:
- C4028
ms.assetid: c3e8b70b-e870-416c-a285-bba5f71dbfc6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b6c71f04b8f0829bbc321d38a18e4307df51ff0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054736"
---
# <a name="compiler-warning-level-1-c4028"></a>編譯器警告 （層級 1） C4028

型式參數 'number' 宣告不同

型式參數的型別不一致的宣告中的對應參數。 會使用原始宣告中的型別。

這個警告只適用於 C 原始程式碼。

## <a name="example"></a>範例

下列範例會產生 C4028。

```
// C4028.c
// compile with: /W1 /Za
void f(int , ...);
void f(int i, int j) {}   // C4028

void g(int , int);
void g(int i, int j) {}   // OK

int main() {}
```
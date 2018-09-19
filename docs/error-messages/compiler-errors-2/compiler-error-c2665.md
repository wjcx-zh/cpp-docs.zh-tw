---
title: 編譯器錯誤 C2665 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2665
dev_langs:
- C++
helpviewer_keywords:
- C2665
ms.assetid: a7f99b61-2eae-4f2b-ba75-ea68fd1e8312
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b442e1de0481ef3d00742ed201575526332decff
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109141"
---
# <a name="compiler-error-c2665"></a>編譯器錯誤 C2665

'function': 沒有任何數字 1 多載可以轉換參數數字 2，從類型 'type'

多載函式的參數無法轉換為要求的類型。  可能的解決方式：

- 提供轉換運算子。

- 使用明確轉換。

## <a name="example"></a>範例

下列範例會產生 C2665。

```
// C2665.cpp
void func(short, char*){}
void func(char*, char*){}

int main() {
   func(0, 1);   // C2665
   func((short)0, (char*)1);   // OK
}
```
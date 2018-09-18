---
title: 編譯器錯誤 C3286 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3286
dev_langs:
- C++
helpviewer_keywords:
- C3286
ms.assetid: 554328c8-cf44-4f7d-a8d2-def74d28ecdd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9ea2a6dcccd6de6d4fc3081106123f4ab37f71a2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052909"
---
# <a name="compiler-error-c3286"></a>編譯器錯誤 C3286

> '*規範*': 反覆運算變數不能有任何儲存類別規範

儲存類別不能指定反覆項目變數。 如需詳細資訊，請參閱 <<c0> [ 儲存類別 （c + +）](../../cpp/storage-classes-cpp.md)並[分別在](../../dotnet/for-each-in.md)。

## <a name="example"></a>範例

下列範例會產生 c3286:，，和也會示範正確使用方式。

```cpp
// C3286.cpp
// compile with: /clr
int main() {
   array<int> ^p = { 1, 2, 3 };
   for each (static int i in p) {}   // C3286
   for each (int j in p) {}   // OK
}
```
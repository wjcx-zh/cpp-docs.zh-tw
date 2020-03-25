---
title: 編譯器錯誤 C3286
ms.date: 11/04/2016
f1_keywords:
- C3286
helpviewer_keywords:
- C3286
ms.assetid: 554328c8-cf44-4f7d-a8d2-def74d28ecdd
ms.openlocfilehash: 4c87e98f11a560d0d92be8ea7bc624edd4e09ad2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201392"
---
# <a name="compiler-error-c3286"></a>編譯器錯誤 C3286

> '*規範*'：反覆運算變數不能有任何儲存類別指定名稱

無法在反復專案變數上指定儲存類別。 如需詳細資訊，請參閱[中](../../dotnet/for-each-in.md)的[儲存類別（C++）](../../cpp/storage-classes-cpp.md)和。

## <a name="example"></a>範例

下列範例會產生 C3286，而且也會顯示正確的使用方式。

```cpp
// C3286.cpp
// compile with: /clr
int main() {
   array<int> ^p = { 1, 2, 3 };
   for each (static int i in p) {}   // C3286
   for each (int j in p) {}   // OK
}
```

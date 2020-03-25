---
title: 編譯器警告 (層級 3) C4267
ms.date: 11/04/2016
f1_keywords:
- C4267
helpviewer_keywords:
- C4267
ms.assetid: 2fa2f13f-fa4f-47bb-ad8f-6cb19cfc91e6
ms.openlocfilehash: 2ae4b53dfa5050e178bf5ddd366e97c4ff773dd0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161512"
---
# <a name="compiler-warning-level-3-c4267"></a>編譯器警告 (層級 3) C4267

'var': 將 'size_t' 轉換為 'type'，資料可能遺失

編譯器偵測到從 `size_t` 轉換成較小的類型。

若要修正這項警告，請使用 `size_t`，而不是 `type`。 或者，使用至少與 `size_t` 一樣大的整數類型。

## <a name="example"></a>範例

下列範例會產生 C4267：

```cpp
// C4267.cpp
// compile by using: cl /W4 C4267.cpp
void Func1(short) {}
void Func2(int) {}
void Func3(long) {}
void Func4(size_t) {}

int main() {
   size_t bufferSize = 10;
   Func1(bufferSize);   // C4267 for all platforms
   Func2(bufferSize);   // C4267 only for 64-bit platforms
   Func3(bufferSize);   // C4267 only for 64-bit platforms
   Func4(bufferSize);   // OK for all platforms
}
```

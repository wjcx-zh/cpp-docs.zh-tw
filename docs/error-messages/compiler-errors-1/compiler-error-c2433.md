---
title: 編譯器錯誤 C2433
ms.date: 11/04/2016
f1_keywords:
- C2433
helpviewer_keywords:
- C2433
ms.assetid: 7079fedd-6059-4125-82ef-ebe275f1f9d1
ms.openlocfilehash: f8cd8d5c165b796dff5260e84a505356f2a74941
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216215"
---
# <a name="compiler-error-c2433"></a>編譯器錯誤 C2433

' identifier '：在資料宣告上不允許 ' 修飾詞 '

**`friend`**、 **`virtual`** 和修飾詞 **`inline`** 不能用於資料宣告。

## <a name="example"></a>範例

下列範例會產生 C2433。

```cpp
// C2433.cpp
class C{};

int main() {
   inline C c;   // C2433
}
```

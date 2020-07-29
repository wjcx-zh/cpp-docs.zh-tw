---
title: 編譯器錯誤 C2390
ms.date: 11/04/2016
f1_keywords:
- C2390
helpviewer_keywords:
- C2390
ms.assetid: 06b749ee-d072-4db1-b229-715f2c0728b5
ms.openlocfilehash: 48012c0fe31b2017cad29cc98992c9b1121efa7c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221181"
---
# <a name="compiler-error-c2390"></a>編譯器錯誤 C2390

' identifier '：不正確的儲存類別 ' 規範 '

儲存類別對全域範圍識別碼而言是不正確。 預設的儲存類別會用來取代不正確類別。

可能的解決方式：

- 如果識別碼是函式，請使用儲存體來宣告 **`extern`** 。

- 如果識別碼是型式參數或區域變數，請將它宣告為自動儲存。

- 如果識別碼是全域變數，請將它宣告為沒有儲存類別（自動儲存）。

## <a name="example"></a>範例

- 下列範例會產生 C2390：

```cpp
// C2390.cpp
register int i;   // C2390

int main() {
   register int j;   // OK
}
```

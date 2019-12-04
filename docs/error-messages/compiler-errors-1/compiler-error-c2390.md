---
title: 編譯器錯誤 C2390
ms.date: 11/04/2016
f1_keywords:
- C2390
helpviewer_keywords:
- C2390
ms.assetid: 06b749ee-d072-4db1-b229-715f2c0728b5
ms.openlocfilehash: 515e2e151d27dd2eb84fc1dc71b9197b36b14cbb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745040"
---
# <a name="compiler-error-c2390"></a>編譯器錯誤 C2390

' identifier '：不正確的儲存類別 ' 規範 '

儲存類別對全域範圍識別碼而言是不正確。 預設的儲存類別會用來取代不正確類別。

可能的解決方式：

- 如果識別碼是函式，請使用 `extern` 儲存體來宣告它。

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

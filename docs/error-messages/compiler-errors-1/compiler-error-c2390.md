---
title: 編譯器錯誤 C2390
ms.date: 11/04/2016
f1_keywords:
- C2390
helpviewer_keywords:
- C2390
ms.assetid: 06b749ee-d072-4db1-b229-715f2c0728b5
ms.openlocfilehash: 89f6ebb02326413e8dca67d333e555321da4e645
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50595867"
---
# <a name="compiler-error-c2390"></a>編譯器錯誤 C2390

'identifier': 不正確的儲存類別 'specifier'

儲存類別不是適用於全域範圍識別項。 預設儲存體類別用來取代無效的類別。

可能的解決方式：

- 如果識別項是函數，將它與宣告`extern`儲存體。

- 如果識別項是型式參數或區域變數，請將它宣告具有自動儲存體。

- 如果識別碼的全域變數，請將它宣告使用沒有儲存類別 （自動儲存體）。

## <a name="example"></a>範例

- 下列範例會產生 C2390:

```
// C2390.cpp
register int i;   // C2390

int main() {
   register int j;   // OK
}
```
---
title: 編譯器錯誤 C2433
ms.date: 11/04/2016
f1_keywords:
- C2433
helpviewer_keywords:
- C2433
ms.assetid: 7079fedd-6059-4125-82ef-ebe275f1f9d1
ms.openlocfilehash: 8a98fcf7570605694569b7ae466ae0a3c7cf14bb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166733"
---
# <a name="compiler-error-c2433"></a>編譯器錯誤 C2433

'identifier': 'modifier' 不允許在資料宣告上

`friend`， `virtual`，和`inline`修飾詞不能用於資料宣告。

## <a name="example"></a>範例

下列範例會產生 C2433。

```
// C2433.cpp
class C{};

int main() {
   inline C c;   // C2433
}
```
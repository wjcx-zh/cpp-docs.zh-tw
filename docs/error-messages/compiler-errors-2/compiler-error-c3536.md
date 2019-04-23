---
title: 編譯器錯誤 C3536
ms.date: 11/04/2016
f1_keywords:
- C3536
helpviewer_keywords:
- C3536
ms.assetid: 8d866075-866b-49eb-9979-ee27b308f7e3
ms.openlocfilehash: a16c5bd46d806d09861d5734b637c2c9d9b2f9d0
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59031891"
---
# <a name="compiler-error-c3536"></a>編譯器錯誤 C3536

'symbol': 無法在初始化之前使用。

在初始化之前，無法使用指定的符號。 實際上，這表示不能使用變數來初始化它自己。

### <a name="to-correct-this-error"></a>更正這個錯誤

1. 未初始化的變數本身。

## <a name="example"></a>範例

下列範例會產生 C3536，因為每個變數使用本身進行初始化。

```
// C3536.cpp
// Compile with /Zc:auto
int main()
{
   auto a = a;     //C3536
   auto b = &b;    //C3536
   auto c = c + 1; //C3536
   auto* d = &d;   //C3536
   auto& e = e;    //C3536
   return 0;
};
```

## <a name="see-also"></a>另請參閱

[auto 關鍵字](../../cpp/auto-keyword.md)
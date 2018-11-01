---
title: 編譯器錯誤 C3087
ms.date: 11/04/2016
f1_keywords:
- C3087
helpviewer_keywords:
- C3087
ms.assetid: 4f5bdd52-a853-4f02-b160-6868e9190b9d
ms.openlocfilehash: 43044e0708ce9c30099c7d25935a8ff9605f45ca
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50489710"
---
# <a name="compiler-error-c3087"></a>編譯器錯誤 C3087

'named_argument: 'attribute' 的呼叫已將此成員初始化

具名引數指定在與相同值之未命名引數的相同屬性區塊中。 請只指定具名或未命名的引數。

## <a name="example"></a>範例

下列範例會產生 C3087：

```
// C3087.cpp
// compile with: /c
[idl_quote("quote1", text="quote2")];   // C3087
[idl_quote(text="quote3")];   // OK
[idl_quote("quote4")];   // OK
```
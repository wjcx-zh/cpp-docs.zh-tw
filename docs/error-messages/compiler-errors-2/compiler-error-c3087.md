---
title: 編譯器錯誤 C3087 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3087
dev_langs:
- C++
helpviewer_keywords:
- C3087
ms.assetid: 4f5bdd52-a853-4f02-b160-6868e9190b9d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9a95b14df3701d26a249e8e0d0e8ec4bafe5eb0d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46041606"
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
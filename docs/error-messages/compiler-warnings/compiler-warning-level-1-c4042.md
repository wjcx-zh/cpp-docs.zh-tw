---
title: 編譯器警告 （層級 1） C4042 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4042
dev_langs:
- C++
helpviewer_keywords:
- C4042
ms.assetid: e4bd861b-1194-426b-bf79-68c5b021eb0a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5bef2071cf31123b5b172df2651c0d6a6d87d4fc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067465"
---
# <a name="compiler-warning-level-1-c4042"></a>編譯器警告 （層級 1） C4042

'identifier': 具有不正確的儲存體類別

指定的儲存體類別不能使用這個識別碼在此內容中。 編譯器會改為使用預設的儲存類別：

- `extern`如果*識別碼*是函式。

- **自動**的話*識別碼*是型式參數或區域變數。

- 沒有儲存體類別，如果*識別碼*是全域變數。

這個警告可能因指定的儲存體類別以外**註冊**在參數宣告中。

下列範例會產生 C4042

```
// C4042.cpp
// compile with: /W1 /LD
int func2( __declspec( thread ) int tls_i )    // C4042
// try the following line instead
// int func2( int tls_i )
{
   return tls_i;
}
```
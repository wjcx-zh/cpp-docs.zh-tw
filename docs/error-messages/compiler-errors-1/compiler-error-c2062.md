---
title: 編譯器錯誤 C2062 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2062
dev_langs:
- C++
helpviewer_keywords:
- C2062
ms.assetid: 6cc98353-2ddf-43ab-88a2-9cc91cdd6033
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bbda0894b25e09681207d6447bb40727d490fc02
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46072240"
---
# <a name="compiler-error-c2062"></a>編譯器錯誤 C2062

類型 'type' 未預期

編譯器未預期的型別名稱。

下列範例會產生 C2062:

```
// C2062.cpp
// compile with: /c
struct A {  : int l; };   // C2062
struct B { private: int l; };   // OK
```

C2062 也可能是因為編譯器的方式控制代碼未定義的類型建構函式的參數清單中。 如果編譯器發現未定義的 （拼字有誤？） 型別時，它會假設建構函式是一個運算式，並發出 C2062。 若要解決，只在建構函式參數清單中使用定義的類型。
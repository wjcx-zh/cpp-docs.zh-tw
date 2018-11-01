---
title: 編譯器錯誤 C2062
ms.date: 11/04/2016
f1_keywords:
- C2062
helpviewer_keywords:
- C2062
ms.assetid: 6cc98353-2ddf-43ab-88a2-9cc91cdd6033
ms.openlocfilehash: dcfac9629a90b82744f87ec105c30301b2102cdf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50601470"
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
---
title: 編譯器錯誤 C2891
ms.date: 11/04/2016
f1_keywords:
- C2891
helpviewer_keywords:
- C2891
ms.assetid: e12cfb2d-df45-4b0d-b155-c51d17e812fa
ms.openlocfilehash: d9a1cdafdf7d3a2843aee4a20f71c7e6a4693150
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50547931"
---
# <a name="compiler-error-c2891"></a>編譯器錯誤 C2891

'parameter': 無法取得樣板參數的位址

您無法取得樣板參數的位址，除非它是左值。 型別參數不是左值，因為它們沒有位址。 不是左值的範本參數清單中的非類型值也沒有位址。 這會是造成編譯器錯誤 C2891，程式碼範例，因為傳遞做為範本參數的值是編譯器產生的複製的樣板引數。

```
template <int i> int* f() { return &i; }
```

都是左值，例如參考類型的範本參數可以有其取得位址。

```
template <int& r> int* f() { return &r; }
```

若要更正這個錯誤，不會為範本參數的位址除非它是左值。
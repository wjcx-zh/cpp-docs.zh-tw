---
title: 編譯器錯誤 C2891
ms.date: 11/04/2016
f1_keywords:
- C2891
helpviewer_keywords:
- C2891
ms.assetid: e12cfb2d-df45-4b0d-b155-c51d17e812fa
ms.openlocfilehash: 2544cfc9e8cff283a7c3e0ace499408bb84cd046
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201629"
---
# <a name="compiler-error-c2891"></a>編譯器錯誤 C2891

' parameter '：無法接受範本參數的位址

您無法接受範本參數的位址，除非它是左值。 類型參數不會左值，因為它們沒有位址。 未左值的範本參數清單中的非類型值也不會有位址。 這是導致編譯器錯誤 C2891 的程式碼範例，因為當做樣板參數傳遞的值是編譯器所產生的樣板引數複本。

```
template <int i> int* f() { return &i; }
```

左值的範本參數（如參考型別）可以取得其位址。

```
template <int& r> int* f() { return &r; }
```

若要更正這個錯誤，請不要接受範本參數的位址，除非它是左值。

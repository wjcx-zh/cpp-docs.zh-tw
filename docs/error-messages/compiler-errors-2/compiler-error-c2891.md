---
title: 編譯器錯誤 C2891 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2891
dev_langs:
- C++
helpviewer_keywords:
- C2891
ms.assetid: e12cfb2d-df45-4b0d-b155-c51d17e812fa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 86d81662cb02fa3c8f6af75009daf4dab9b70196
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016555"
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
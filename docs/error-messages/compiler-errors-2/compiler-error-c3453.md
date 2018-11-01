---
title: 編譯器錯誤 C3453
ms.date: 11/04/2016
f1_keywords:
- C3453
helpviewer_keywords:
- C3453
ms.assetid: dbefdbcf-f697-4239-b7a5-1d99b85e9e7f
ms.openlocfilehash: 2b3288d02c611bf6785ca1ea7757e2283d889050
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472718"
---
# <a name="compiler-error-c3453"></a>編譯器錯誤 C3453

'attribute': 未套用屬性，因為限定詞 'assembly' 不相符

只有組件或模組層級屬性才能指定為獨立指示。

## <a name="example"></a>範例

下列範例會產生 C3453。

```
// C3453.cpp
// compile with: /clr /c
[assembly:System::CLSCompliant(true)]   // C3453
// try the following line instead
// [assembly:System::CLSCompliant(true)];
ref class X {};
```
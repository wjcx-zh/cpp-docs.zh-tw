---
title: 編譯器錯誤 C3895
ms.date: 11/04/2016
f1_keywords:
- C3895
helpviewer_keywords:
- C3895
ms.assetid: 771b9fe5-d6d4-4297-bf57-e2f857722155
ms.openlocfilehash: c4b1cad9ef48f1f16b411aab46e1bb9285d69ff3
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59779293"
---
# <a name="compiler-error-c3895"></a>編譯器錯誤 C3895

'var': 類型資料成員不可為 'volatile'

特定種類的資料成員，例如[常值](../../extensions/literal-cpp-component-extensions.md)或是[initonly](../../dotnet/initonly-cpp-cli.md)，不能[volatile](../../cpp/volatile-cpp.md)。

下列範例會產生 C3895:

```
// C3895.cpp
// compile with: /clr
ref struct Y1 {
   initonly
   volatile int data_var2;   // C3895
};
```
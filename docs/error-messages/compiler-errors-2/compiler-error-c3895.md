---
title: 編譯器錯誤 C3895 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3895
dev_langs:
- C++
helpviewer_keywords:
- C3895
ms.assetid: 771b9fe5-d6d4-4297-bf57-e2f857722155
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3a722ac9091e47db95bcc3e2d81293bf662d0c99
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033286"
---
# <a name="compiler-error-c3895"></a>編譯器錯誤 C3895

'var': 類型資料成員不可為 'volatile'

特定種類的資料成員，例如[常值](../../windows/literal-cpp-component-extensions.md)或是[initonly](../../dotnet/initonly-cpp-cli.md)，不能[volatile](../../cpp/volatile-cpp.md)。

下列範例會產生 C3895:

```
// C3895.cpp
// compile with: /clr
ref struct Y1 {
   initonly
   volatile int data_var2;   // C3895
};
```
---
title: 嚴重錯誤 C1104
ms.date: 11/04/2016
f1_keywords:
- C1104
helpviewer_keywords:
- C1104
ms.assetid: 45bd85c4-77d3-4d3c-b167-49c563aefb4d
ms.openlocfilehash: c10d1a89d854aaeac47a9a70f1e1e319d1662935
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50520273"
---
# <a name="fatal-error-c1104"></a>嚴重錯誤 C1104

匯入 libid 時發生嚴重錯誤：'message'

編譯器偵測到匯入類型程式庫時發生問題。  例如，您無法使用 libid 來指定類型程式庫，同時又指定 `no_registry`。

如需詳細資訊，請參閱 < [#import 指示詞](../../preprocessor/hash-import-directive-cpp.md)。

下列範例會產生 C1104：

```
// C1104.cpp
#import "libid:11111111.1111.1111.1111.111111111111" version("4.0") lcid("9") no_registry auto_search   // C1104
```
---
title: 嚴重錯誤 C1104
ms.date: 11/04/2016
f1_keywords:
- C1104
helpviewer_keywords:
- C1104
ms.assetid: 45bd85c4-77d3-4d3c-b167-49c563aefb4d
ms.openlocfilehash: a26e65e98b44a69eb14daf6d835fafb23362dfa2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747328"
---
# <a name="fatal-error-c1104"></a>嚴重錯誤 C1104

匯入 libid 時發生嚴重錯誤：'message'

編譯器偵測到匯入類型程式庫時發生問題。  例如，您無法使用 libid 來指定類型程式庫，同時又指定 `no_registry`。

如需詳細資訊，請參閱[#import](../../preprocessor/hash-import-directive-cpp.md)指示詞。

下列範例會產生 C1104：

```cpp
// C1104.cpp
#import "libid:11111111.1111.1111.1111.111111111111" version("4.0") lcid("9") no_registry auto_search   // C1104
```

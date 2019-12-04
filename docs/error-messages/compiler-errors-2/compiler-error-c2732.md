---
title: 編譯器錯誤 C2732
ms.date: 11/04/2016
f1_keywords:
- C2732
helpviewer_keywords:
- C2732
ms.assetid: 01b7ad2c-93cf-456f-a4c0-c5f2fdc7c07c
ms.openlocfilehash: 61bac8c1b5c9e029cc5833f458669b490fed8c91
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755794"
---
# <a name="compiler-error-c2732"></a>編譯器錯誤 C2732

連結規格和 'function' 先前的規格衝突

已使用不同的連結規範宣告的函式。

這個錯誤可能是因為包含具有不同連結規範的檔案所造成。

若要修正這個錯誤，請變更 `extern` 陳述式，以便讓連結同意。 尤其，不可包裝 `extern "C"` 區塊中的 `#include` 指示詞。

## <a name="example"></a>範例

下列範例會產生 C2732：

```cpp
// C2732.cpp
extern void func( void );   // implicit C++ linkage
extern "C" void func( void );   // C2732
```

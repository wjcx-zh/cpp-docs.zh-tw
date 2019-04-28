---
title: 編譯器錯誤 C2732
ms.date: 11/04/2016
f1_keywords:
- C2732
helpviewer_keywords:
- C2732
ms.assetid: 01b7ad2c-93cf-456f-a4c0-c5f2fdc7c07c
ms.openlocfilehash: 820a620b7e4414123c56433f84536393834f6fd6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208398"
---
# <a name="compiler-error-c2732"></a>編譯器錯誤 C2732

連結規格和 'function' 先前的規格衝突

已使用不同的連結規範宣告的函式。

這個錯誤可能是因為包含具有不同連結規範的檔案所造成。

若要修正這個錯誤，請變更 `extern` 陳述式，以便讓連結同意。 尤其，不可包裝 `extern "C"` 區塊中的 `#include` 指示詞。

## <a name="example"></a>範例

下列範例會產生 C2732：

```
// C2732.cpp
extern void func( void );   // implicit C++ linkage
extern "C" void func( void );   // C2732
```
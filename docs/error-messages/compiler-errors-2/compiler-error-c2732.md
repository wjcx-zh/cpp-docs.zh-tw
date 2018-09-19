---
title: 編譯器錯誤 C2732 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2732
dev_langs:
- C++
helpviewer_keywords:
- C2732
ms.assetid: 01b7ad2c-93cf-456f-a4c0-c5f2fdc7c07c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 040fd73bcb69ef032d5c6150bb157337f34a2088
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079657"
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
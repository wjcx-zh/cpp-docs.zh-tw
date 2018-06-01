---
title: 編譯器警告 C4956 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4956
dev_langs:
- C++
helpviewer_keywords:
- C4956
ms.assetid: 9154f2d1-d49f-4e07-90d2-0e9bc028011a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: be92eb948e31a0a5367f92f5c2ed59baac2bd39b
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2018
ms.locfileid: "34703700"
---
# <a name="compiler-warning-c4956"></a>編譯器警告 C4956

> '*類型*': 這個類型不是可驗證

## <a name="remarks"></a>備註

指定 [/clr:safe](../../build/reference/clr-common-language-runtime-compilation.md) 且您的程式碼包含無法驗證的類型時，就會產生這個警告。 **/Clr: safe**編譯器選項已被取代 Visual Studio 2015 中，在 Visual Studio 2017 中支援。

如需詳細資訊，請參閱[純粹的和可驗證程式碼 (C + + /CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。

發出這個警告即表示發生錯誤，而且可以使用 [warning](../../preprocessor/warning.md) pragma 或 [/wd](../../build/reference/compiler-option-warning-level.md) 編譯器選項予以停用。

## <a name="example"></a>範例

下列範例會產生 C4956：

```cpp
// C4956.cpp
// compile with: /clr:safe
int* p;   // C4956
```
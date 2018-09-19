---
title: 編譯器警告 C4335 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4335
dev_langs:
- C++
helpviewer_keywords:
- C4335
ms.assetid: e66467ad-a10b-4438-8c7c-e8e8d11d39bb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d2b28909d0c4b663fffeacbec58ad694131bb008
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036575"
---
# <a name="compiler-warning-c4335"></a>編譯器警告 C4335

偵測到 Mac 檔案格式： 請將原始程式檔轉換為 DOS 或 UNIX 格式

行結束字元的原始程式檔的第一行是相對於 UNIX ('\n') 或 DOS ('\r\n') 的 Macintosh 樣式 ('\r')。

永遠會發出這個警告，以發出。  請參閱[警告](../../preprocessor/warning.md)如需如何停用此警告的 pragma。  此外，會發出這個警告只一次每個編譯。 因此，如果有多個`#include`Macintosh 格式來指定檔案的指示詞，C4335 只會發佈一次。

Macintosh 格式產生檔案的一種方法是使用**進階儲存選項**(在**檔案**功能表) 在 Visual Studio 中。

## <a name="example"></a>範例

下列範例會產生 C4335。

```
// C4335 expected
#include "c4335.h"   // assume both include files are in Macintosh format
#include "c4335_2.h"
```
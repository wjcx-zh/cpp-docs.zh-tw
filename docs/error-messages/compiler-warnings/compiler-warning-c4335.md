---
title: 編譯器警告 C4335
ms.date: 11/04/2016
f1_keywords:
- C4335
helpviewer_keywords:
- C4335
ms.assetid: e66467ad-a10b-4438-8c7c-e8e8d11d39bb
ms.openlocfilehash: 43c2f5d9092cdbad14e429349bd7d04e236b75e4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447277"
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
---
title: 編譯器警告 C4335
ms.date: 11/04/2016
f1_keywords:
- C4335
helpviewer_keywords:
- C4335
ms.assetid: e66467ad-a10b-4438-8c7c-e8e8d11d39bb
ms.openlocfilehash: ccb00118d0c6895eee84976bb01472ea2f98353d
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627127"
---
# <a name="compiler-warning-c4335"></a>編譯器警告 C4335

偵測到 Mac 檔案格式：請將來源檔案轉換成 DOS 或 UNIX 格式

原始程式檔第一行的行終止字元是 Macintosh 樣式（' \r '），而不是 UNIX （' \n '）或 DOS （' \r\n '）。

此警告一律會發出為錯誤。  如需如何停用此警告的相關資訊，請參閱[warning](../../preprocessor/warning.md) pragma。  此外，此警告只會針對每個編譯模組發出一次。 因此，如果有多個 `#include` 指示詞指定 Macintosh 格式的檔案，則只會發出一次 C4335。

以 Macintosh 格式產生檔案的其中一種方式是使用 Visual Studio**中的 [** **高級儲存] 選項**（在 [檔案] 功能表上）。

## <a name="example"></a>範例

下列範例會產生 C4335。

```cpp
// C4335 expected
#include "c4335.h"   // assume both include files are in Macintosh format
#include "c4335_2.h"
```

---
title: include_alias pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.include_alias
- include_alias_CPP
helpviewer_keywords:
- pragmas, include_alias
- include_alias pragma
ms.assetid: 3256d589-12b3-4af0-a586-199e96eabacc
ms.openlocfilehash: aa3714186e8f95d4044ba5a3b2bc2d5fcfb1fc9c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218899"
---
# <a name="include_alias-pragma"></a>include_alias pragma

指定在指示詞中`#include`找到 alias_filename 時, 編譯器會在其位置取代*actual_filename* 。

## <a name="syntax"></a>語法

<!-- localization note - it's important to have the italic and bold characters immediately adjacent here. -->
> **#pragma include_alias (** "*alias_filename*" **,** "*actual_filename*" **)** \
> **#pragma include_alias (** \< *alias_filename* >  **,** *actual_filename*) \< > 

## <a name="remarks"></a>備註

**Include_alias** pragma 指示詞可讓您將具有不同名稱或路徑的檔案替換成原始程式檔所包含的檔案名。 例如, 某些檔案系統所允許的標標頭檔名會比 8.3 FAT 檔案系統限制更長。 編譯器無法將較長的名稱截斷為 8.3, 因為較長標標頭檔名的前八個字元可能不是唯一的。 每當編譯器在指示詞中`#include`看到 alias_filename 字串時, 就會改為替代名稱*actual_filename* 。 然後它會載入*actual_filename*標頭檔。 這個 pragma 必須出現在對應的 `#include` 指示詞前面。 例如：

```cpp
// First eight characters of these two files not unique.
#pragma include_alias( "AppleSystemHeaderQuickdraw.h", "quickdra.h" )
#pragma include_alias( "AppleSystemHeaderFruit.h", "fruit.h" )

#pragma include_alias( "GraphicsMenu.h", "gramenu.h" )

#include "AppleSystemHeaderQuickdraw.h"
#include "AppleSystemHeaderFruit.h"
#include "GraphicsMenu.h"
```

要搜尋的別名必須完全符合規格。 案例、拼寫和雙引號或角括弧的使用都必須相符。 **Include_alias** pragma 會對檔案名進行簡單的字串比對。 不會執行其他檔案名驗證。 例如，假設有下列指示詞：

```cpp
#pragma include_alias("mymath.h", "math.h")
#include "./mymath.h"
#include "sys/mymath.h"
```

因為標頭檔字串不完全相符, 所以不會執行任何別名替代。 此外, 用來`/Yu`做為和`/Yc` `hdrstop`編譯器選項之引數的標標頭檔名, 或 pragma 也不會被取代。 例如，如果原始程式檔包含下列指示詞：

```cpp
#include <AppleSystemHeaderStop.h>
```

則對應的編譯器選項應該是

> **/YcAppleSystemHeaderStop.h**

您可以使用**include_alias** pragma 將任何標標頭檔名對應至另一個。 例如：

```cpp
#pragma include_alias( "api.h", "c:\version1.0\api.h" )
#pragma include_alias( <stdio.h>, <newstdio.h> )
#include "api.h"
#include <stdio.h>
```

請勿混用雙引號括住的檔案名與以角括弧括住的檔案名。 例如, 假設上述兩個`#pragma include_alias`指示詞, 編譯器不會對下列`#include`指示詞進行替代:

```cpp
#include <api.h>
#include "stdio.h"
```

此外，下列指示詞會產生錯誤：

```cpp
#pragma include_alias(<header.h>, "header.h")  // Error
```

錯誤訊息中所報告的檔案名, 或做為預先定義`__FILE__`宏的值, 是在替代完成後的檔案名。 例如, 請參閱下列指示詞之後的輸出:

```cpp
#pragma include_alias( "VERYLONGFILENAME.H", "myfile.h" )
#include "VERYLONGFILENAME.H"
```

VERYLONGFILENAME 發生錯誤 *。H*會產生下列錯誤訊息:

```Output
myfile.h(15) : error C2059 : syntax error
```

另請注意, 不支援傳遞。 假設有下列指示詞：

```cpp
#pragma include_alias( "one.h", "two.h" )
#pragma include_alias( "two.h", "three.h" )
#include "one.h"
```

編譯器會搜尋檔案 two,而不是*3. h*。

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)

---
title: include_alias
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.include_alias
- include_alias_CPP
helpviewer_keywords:
- pragmas, include_alias
- include_alias pragma
ms.assetid: 3256d589-12b3-4af0-a586-199e96eabacc
ms.openlocfilehash: 616672d713a9f0ac6eab4be8bce9b178d2510723
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50573159"
---
# <a name="includealias"></a>include_alias

指定*short_filename*是要做為別名*long_filename*。

## <a name="syntax"></a>語法

> #<a name="pragma-includealiaslongfilename-shortfilename"></a>pragma include_alias (「*long_filename*"，"*short_filename*")
> #<a name="pragma-includealiaslongfilename-shortfilename"></a>pragma include_alias (*long_filename*， *short_filename*)

## <a name="remarks"></a>備註

有些檔案系統可使用比 8.3 FAT 檔案系統所限制更長的標頭檔名稱。 由於較長標頭檔名稱的前八個字元不一定是唯一的，因此編譯器無法依照 8.3 的限制直接截斷較長的名稱。 只要編譯器遇到*long_filename*字串，它會替代*short_filename*，並尋找標頭檔*short_filename*改。 這個 pragma 必須出現在對應的 `#include` 指示詞前面。 例如: 

```cpp
// First eight characters of these two files not unique.
#pragma include_alias( "AppleSystemHeaderQuickdraw.h", "quickdra.h" )
#pragma include_alias( "AppleSystemHeaderFruit.h", "fruit.h" )

#pragma include_alias( "GraphicsMenu.h", "gramenu.h" )

#include "AppleSystemHeaderQuickdraw.h"
#include "AppleSystemHeaderFruit.h"
#include "GraphicsMenu.h"
```

要搜尋的別名無論大小寫、拼字和雙引號或角括號的用法，都必須完全符合規格。 **Include_alias** pragma 會執行簡單比對的檔案名稱的字串，會執行任何其他的檔案名稱驗證。 例如，假設有下列指示詞：

```cpp
#pragma include_alias("mymath.h", "math.h")
#include "./mymath.h"
#include "sys/mymath.h"
```

不會設定別名 (替代)，因為標頭檔字串並非完全相符。 此外，作為引數使用的標頭檔名`/Yu`並`/Yc`編譯器選項或`hdrstop`pragma，不會被取代。 例如，如果原始程式檔包含下列指示詞：

```cpp
#include <AppleSystemHeaderStop.h>
```

則對應的編譯器選項應該是

> /YcAppleSystemHeaderStop.h

您可以使用**include_alias** pragma，來將任何標頭檔名稱對應至另一個。 例如: 

```cpp
#pragma include_alias( "api.h", "c:\version1.0\api.h" )
#pragma include_alias( <stdio.h>, <newstdio.h> )
#include "api.h"
#include <stdio.h>
```

請勿將使用雙引號含括的檔案名稱與使用角括號含括的檔案名稱混用。 例如，假設上述的兩個`#pragma include_alias`指示詞，編譯器會對下列中的替代項目`#include`指示詞：

```cpp
#include <api.h>
#include "stdio.h"
```

此外，下列指示詞會產生錯誤：

```cpp
#pragma include_alias(<header.h>, "header.h")  // Error
```

請注意，檔案名稱會報告錯誤訊息，或做為預先定義的值`__FILE__`巨集，在執行替代之後是檔案的名稱。 例如，下列指示詞之後看到輸出：

```cpp
#pragma include_alias( "VeryLongFileName.H", "myfile.h" )
#include "VeryLongFileName.H"
```

VERYLONGFILENAME 時發生錯誤。H 會產生下列錯誤訊息：

```Output
myfile.h(15) : error C2059 : syntax error
```

另請注意，目前不支援轉移。 假設有下列指示詞：

```cpp
#pragma include_alias( "one.h", "two.h" )
#pragma include_alias( "two.h", "three.h" )
#include "one.h"
```

編譯器會搜尋 TWO.H 這個檔案，而不是 THREE.H。

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
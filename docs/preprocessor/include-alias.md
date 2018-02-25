---
title: "include_alias |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc-pragma.include_alias
- include_alias_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, include_alias
- include_alias pragma
ms.assetid: 3256d589-12b3-4af0-a586-199e96eabacc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5a2e3b6f6b8bbbc17073b5bf43b54fff3a619793
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="includealias"></a>include_alias

指定*short_filename*是要做為別名*long_filename*。

## <a name="syntax"></a>語法

> #<a name="pragma-includealiaslongfilename-shortfilename"></a>pragma include_alias("*long_filename*", "*short_filename*")  
> #<a name="pragma-includealiaslongfilename-shortfilename"></a>pragma include_alias (*long_filename*， *short_filename*)

## <a name="remarks"></a>備註

有些檔案系統可使用比 8.3 FAT 檔案系統所限制更長的標頭檔名稱。 由於較長標頭檔名稱的前八個字元不一定是唯一的，因此編譯器無法依照 8.3 的限制直接截斷較長的名稱。 只要編譯器遇到*long_filename*字串，以取代*short_filename*，並尋找標頭檔*short_filename*改為。 這個 pragma 必須出現在對應的 `#include` 指示詞前面。 例如: 

```cpp
// First eight characters of these two files not unique.
#pragma include_alias( "AppleSystemHeaderQuickdraw.h", "quickdra.h" )
#pragma include_alias( "AppleSystemHeaderFruit.h", "fruit.h" )

#pragma include_alias( "GraphicsMenu.h", "gramenu.h" )

#include "AppleSystemHeaderQuickdraw.h"
#include "AppleSystemHeaderFruit.h"
#include "GraphicsMenu.h"
```

要搜尋的別名無論大小寫、拼字和雙引號或角括號的用法，都必須完全符合規格。 **Include_alias** pragma 會在檔案名稱進行比對的簡單字串，則會執行任何其他檔案名稱驗證。 例如，假設有下列指示詞：

```cpp
#pragma include_alias("mymath.h", "math.h")
#include "./mymath.h"
#include "sys/mymath.h"
```

不會設定別名 (替代)，因為標頭檔字串並非完全相符。 此外，做為 /Yu 和 /Yc 編譯器選項的引數使用的標頭檔名稱或**hdrstop** pragma，不會被取代。 例如，如果原始程式檔包含下列指示詞：
  
```cpp
#include <AppleSystemHeaderStop.h>
```

則對應的編譯器選項應該是

> /YcAppleSystemHeaderStop.h

您可以使用**include_alias** pragma，來對應至另一個的任何標頭檔名稱。 例如: 

```cpp
#pragma include_alias( "api.h", "c:\version1.0\api.h" )
#pragma include_alias( <stdio.h>, <newstdio.h> )
#include "api.h"
#include <stdio.h>
```

請勿將使用雙引號含括的檔案名稱與使用角括號含括的檔案名稱混用。 例如，假設上述兩個**#pragma include_alias**指示詞，編譯器會在下列執行替代`#include`指示詞：

```cpp
#include <api.h>
#include "stdio.h"
```

此外，下列指示詞會產生錯誤：

```cpp
#pragma include_alias(<header.h>, "header.h")  // Error
```

請注意，filename 報告中的錯誤訊息，或做為預先定義的值**&#95; &#95;檔案 #95; &#95;**巨集，在執行替代之後是檔案的名稱。 例如，下列指示詞之後看到輸出：

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

## <a name="see-also"></a>請參閱

[Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
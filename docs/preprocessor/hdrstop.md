---
title: hdrstop pragma
ms.date: 08/29/2019
f1_keywords:
- hdrstop_CPP
- vc-pragma.hdrstop
helpviewer_keywords:
- hdrstop pragma
- pragmas, hdrstop
ms.assetid: 5ea8370a-10d1-4538-ade6-4c841185da0e
ms.openlocfilehash: f540f0f01fe654213af15afa8fbf5cbd94e4b7e2
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221026"
---
# <a name="hdrstop-pragma"></a>hdrstop pragma

可讓您進一步控制預先編譯的檔案名, 以及儲存編譯狀態的位置。

## <a name="syntax"></a>語法

> **#pragma hdrstop**[("*filename*")]

## <a name="remarks"></a>備註

*Filename*是要使用或建立之先行編譯標頭檔的名稱 (取決於是否指定[/yu](../build/reference/yu-use-precompiled-header-file.md)或[/yc](../build/reference/yc-create-precompiled-header-file.md) )。 如果*filename*不包含路徑規格, 則會假設先行編譯標頭檔位於與來源檔案相同的目錄中。

如果 C 或C++檔案包含以編譯 `/Yc`時的 hdrstop pragma, 編譯器會將編譯的狀態儲存到 pragma 的位置。 不會儲存任何遵循 pragma 之程式碼的編譯狀態。

使用*filename*來命名已編譯狀態儲存所在的先行編譯標頭檔。 **Hdrstop**與*filename*之間的空格是選擇性的。 **Hdrstop** pragma 中指定的檔案名是字串, 因此受限於任何 C 或C++字串的條件約束。 請特別注意，您必須使用引號將其括住，以及使用逸出字元 (反斜線) 來指定目錄名稱。 例如：

```C
#pragma hdrstop( "c:\\projects\\include\\myinc.pch" )
```

先行編譯標頭檔的名稱是根據下列規則來決定的，依照優先順序列出：

1. `/Fp`編譯器選項的引數

2. 的*filename*引數`#pragma hdrstop`

3. 原始程式檔副檔名為 .PCH 的主檔名。

`/Yc`針對和`/Yu`選項, 如果兩個編譯選項或**hdrstop** pragma 都未指定檔案名, 則會使用原始程式檔的基底名稱做為先行編譯標頭檔的基底名稱。

您也可以使用前置處理命令來執行巨集取代，如下所示：

```C
#define INCLUDE_PATH "c:\\progra~`1\\devstsu~1\\vc\\include\\"
#define PCH_FNAME "PROG.PCH"
.
.
.
#pragma hdrstop( INCLUDE_PATH PCH_FNAME )
```

下列規則會管理可放置**hdrstop** pragma 的位置:

- 它必須出現在所有資料或函式宣告或定義的外部。

- 且必須在原始程式檔中，而不在標頭檔中指定。

## <a name="example"></a>範例

```C
#include <windows.h>                 // Include several files
#include "myhdr.h"

__inline Disp( char *szToDisplay )   // Define an inline function
{
    // ...                           // Some code to display string
}
#pragma hdrstop
```

在此範例中, **hdrstop** pragma 會在包含兩個檔案且已定義內嵌函數之後出現。 這個位置一開始可能會是 pragma 的奇數位置。 不過, 請考慮使用手動先行編譯選項, `/Yc`並`/Yu`使用**hdrstop** pragma, 讓您可以先行編譯整個原始程式檔, 甚至是內嵌程式碼。 Microsoft 編譯器並不會限制您只先行編譯資料宣告。

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)

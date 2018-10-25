---
title: hdrstop |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- hdrstop_CPP
- vc-pragma.hdrstop
dev_langs:
- C++
helpviewer_keywords:
- hdrstop pragma
- pragmas, hdrstop
ms.assetid: 5ea8370a-10d1-4538-ade6-4c841185da0e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0e571229602a311633fc7425384544c53813b935
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50059710"
---
# <a name="hdrstop"></a>hdrstop
讓您對先行編譯檔案名稱，以及儲存編譯狀態之位置進行其他控制。

## <a name="syntax"></a>語法

```
#pragma hdrstop [( "filename" )]
```

## <a name="remarks"></a>備註

*檔名*是要使用或建立先行編譯標頭檔的名稱 (取決於是否[/Yu](../build/reference/yu-use-precompiled-header-file.md)或是[/Yc](../build/reference/yc-create-precompiled-header-file.md)指定)。 如果*filename*不包含路徑規格，會假設先行編譯標頭檔中的原始程式檔相同的目錄。

如果 C 或 c + + 檔案包含**hdrstop**編譯時的 pragma `/Yc`，編譯器儲存編譯的 pragma 的位置的狀態。 pragma 後方任何程式碼的編譯狀態都不會儲存。

使用*filename*在其中儲存編譯的狀態的先行編譯標頭檔命名。 之間的空格**hdrstop**並*filename*是選擇性的。 在指定的檔名**hdrstop** pragma 是字串，因此受限於的任何 C 或 c + + 字串條件約束。 請特別注意，您必須使用引號將其括住，以及使用逸出字元 (反斜線) 來指定目錄名稱。 例如: 

```
#pragma hdrstop( "c:\\projects\\include\\myinc.pch" )
```

先行編譯標頭檔的名稱是根據下列規則來決定的，依照優先順序列出：

1. 引數`/Fp`編譯器選項

2. *Filename*引數 `#pragma hdrstop`

3. 原始程式檔副檔名為 .PCH 的主檔名。

針對`/Yc`和`/Yu`選項，如果都不是兩個編譯選項，也不**hdrstop** pragma 中指定的檔案名稱、 原始程式檔的基底名稱做為先行編譯標頭檔的基底名稱。

您也可以使用前置處理命令來執行巨集取代，如下所示：

```
#define INCLUDE_PATH "c:\\progra~`1\\devstsu~1\\vc\\include\\"
#define PCH_FNAME "PROG.PCH"
.
.
.
#pragma hdrstop( INCLUDE_PATH PCH_FNAME )
```

下列規則用於管理**hdrstop**可以放置 pragma:

- 它必須出現在所有資料或函式宣告或定義的外部。

- 且必須在原始程式檔中，而不在標頭檔中指定。

## <a name="example"></a>範例

```
#include <windows.h>                 // Include several files
#include "myhdr.h"

__inline Disp( char *szToDisplay )   // Define an inline function
{
    ...                              // Some code to display string
}
#pragma hdrstop
```

在此範例中， **hdrstop** pragma 出現後兩個檔案已包含及已定義內嵌函式。 一開始可能無法理解為什麼要在這個位置放置 pragma。 考慮，不過，使用手動先行編譯選項，`/Yc`並`/Yu`，使用**hdrstop** pragma 可讓您先行編譯整個原始程式檔，包括內嵌程式碼。 Microsoft 編譯器並不會限制您只先行編譯資料宣告。

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
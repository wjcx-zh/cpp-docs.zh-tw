---
title: _pgmptr、_wpgmptr
ms.date: 11/04/2016
f1_keywords:
- pgmptr
- _pgmptr
- wpgmptr
- _wpgmptr
helpviewer_keywords:
- wpgmptr function
- _wpgmptr function
- _pgmptr function
- pgmptr function
ms.assetid: 4d44b515-0eff-4136-8bc4-684195f218f5
ms.openlocfilehash: beff0401d0aa2aa21819e58618ef4c02795d4393
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75300153"
---
# <a name="_pgmptr-_wpgmptr"></a>_pgmptr、_wpgmptr

可執行檔的路徑。 已被取代，請使用 [_get_pgmptr](../c-runtime-library/reference/get-pgmptr.md) 和 [_get_wpgmptr](../c-runtime-library/reference/get-wpgmptr.md)。

## <a name="syntax"></a>語法

```
extern char *_pgmptr;
extern wchar_t *_wpgmptr;
```

## <a name="remarks"></a>備註

當程式是從命令直譯器 (Cmd.exe) 執行時，`_pgmptr` 會自動針對可執行檔的完整路徑進行初始化。 例如，如果 Hello.exe 位於 C:\BIN 中，且 C:\BIN 位於路徑中，則當您執行下列命令時，`_pgmptr` 便會針對 C:\BIN\Hello.exe 設定：

```
C> hello
```

當程式不是從命令列執行時，`_pgmptr` 可能會針對程式名稱 (不含副檔名的檔案基礎名稱)，或是針對檔案名稱、相對路徑或完整路徑進行初始化。

`_wpgmptr` 是 `_pgmptr` 的寬字元對應版本，適用於使用 `wmain` 的程式。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_tpgmptr`|`_pgmptr`|`_pgmptr`|`_wpgmptr`|

## <a name="requirements"></a>需求

|變數|必要的標頭|
|--------------|---------------------|
|`_pgmptr`、 `_wpgmptr`|\<stdlib.h>|

## <a name="example"></a>範例

下列程式示範 `_pgmptr` 的用法。

```c
// crt_pgmptr.c
// compile with: /W3
// The following program demonstrates the use of _pgmptr.
//
#include <stdio.h>
#include <stdlib.h>
int main( void )
{
   printf("The full path of the executing program is : %Fs\n",
     _pgmptr); // C4996
   // Note: _pgmptr is deprecated; use _get_pgmptr instead
}
```

若要使用 `_wpgmptr`，您可以將 `%Fs` 改為 `%S`，並將 `main` 改為 `wmain`。

## <a name="see-also"></a>請參閱

[全域變數](../c-runtime-library/global-variables.md)

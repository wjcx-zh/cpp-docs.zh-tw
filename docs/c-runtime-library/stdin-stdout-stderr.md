---
title: stdin、stdout、stderr
ms.date: 10/23/2018
f1_keywords:
- stdin
- stderr
- stdout
helpviewer_keywords:
- stdout function
- standard output stream
- standard error stream
- stdin function
- standard input stream
- stderr function
ms.assetid: badd4735-596d-4498-857c-ec8b7e670e4c
ms.openlocfilehash: 5de1ff01282f30ad133f909cb87f5d7c8d521ae5
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57741930"
---
# <a name="stdin-stdout-stderr"></a>stdin、stdout、stderr

## <a name="syntax"></a>語法

```
FILE *stdin;
FILE *stdout;
FILE *stderr;
#include <stdio.h>
```

## <a name="remarks"></a>備註

這些是輸入、輸出和錯誤輸出的標準資料流。

根據預設，標準輸入是從鍵盤讀取，而標準輸出與標準錯誤則會列印至螢幕。

下列資料流指標可用來存取標準資料流：

|Pointer|資料流|
|-------------|------------|
|`stdin`|標準輸入|
|`stdout`|標準輸出|
|`stderr`|標準錯誤|

這些指標可以作為函式的引數使用。 有一些函式 (例如[getchar](../c-runtime-library/reference/getchar-getwchar.md) 及 [putchar](../c-runtime-library/reference/putchar-putwchar.md)) 會自動使用 `stdin` 及 `stdout`。

這些指標是常數，且無法指派新值給它們。 [freopen](../c-runtime-library/reference/freopen-wfreopen.md) 函式可用於將資料流重新導向到磁碟檔案或其他裝置。 作業系統可讓您在命令層級對程式的標準輸入和輸出進行重新導向。

## <a name="see-also"></a>另請參閱

[資料流 I/O](../c-runtime-library/stream-i-o.md)<br/>
[全域常數](../c-runtime-library/global-constants.md)

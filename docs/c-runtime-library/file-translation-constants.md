---
title: 檔案轉譯常數
ms.date: 11/04/2016
f1_keywords:
- c.constants.file
helpviewer_keywords:
- translation constants
- file translation [C++], constants
- translation, file translation constants
- translation, constants
- constants [C++], file translation mode
- file translation [C++]
ms.assetid: 49b13bf3-442e-4d19-878b-bd1029fa666a
ms.openlocfilehash: d98a74c820023ac8684f54413c0e81c58eba7b0b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50443286"
---
# <a name="file-translation-constants"></a>檔案轉譯常數

## <a name="syntax"></a>語法

```
#include <stdio.h>
```

## <a name="remarks"></a>備註

這些常數會指定轉譯的模式 (**"b"** 或 **"t"**)。 該模式會包含在指定存取類型的字串中 (**"r"**、**"w"**、**"a"**、**"r+"**、**"w+"**、**"a+"**)。

轉譯模式如下所示：

- **t**

   以文字 (已轉譯) 模式開啟。 在此模式中，會將歸位字元/換行字元 (CR-LF) 組合會在輸入中轉譯成單行換行字元 (LF)，且會將 LF 字元在輸出中轉譯為 CR-LF 組合。 此外，Ctrl+Z 會在輸入中解譯成檔案結尾字元。 在為了讀取或讀取/寫入而開啟的檔案中，`fopen` 會儘可能檢查檔案結尾是否有 Ctrl+Z 並加以移除。 這樣做的原因是因為使用 `fseek` 和 `ftell` 函式在以 Ctrl+Z 結束的檔案內移動可能會讓 `fseek` 在檔案結尾附近產生不當行為。

   > [!NOTE]
   > **t** 選項並不屬於 `fopen` 和 `freopen` 的 ANSI 標準。 它是 Microsoft 擴充功能，且不應在需要 ANSI 可攜性的情況中使用。

- **b**

   以二進位 (未轉譯) 模式開啟。 會隱藏上述轉譯。

如果 *mode* 中未指定 **t** 或 **b**，則轉譯模式由預設模式變數 [_fmode](../c-runtime-library/fmode.md) 所定義。 如需使用文字和二進位模式的詳細資訊，請參閱[文字和二進位模式檔案 I/O](../c-runtime-library/text-and-binary-mode-file-i-o.md)。

## <a name="see-also"></a>請參閱

[_fdopen、wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)<br/>
[fopen、_wfopen](../c-runtime-library/reference/fopen-wfopen.md)<br/>
f[reopen、_wfreopen](../c-runtime-library/reference/freopen-wfreopen.md)<br/>
[_fsopen、_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)<br/>
[全域常數](../c-runtime-library/global-constants.md)
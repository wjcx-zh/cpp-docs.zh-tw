---
title: 轉譯模式常數
ms.date: 11/04/2016
f1_keywords:
- _O_BINARY
- _O_TEXT
- _O_RAW
helpviewer_keywords:
- O_BINARY constant
- O_TEXT constant
- O_RAW constant
- _O_TEXT constant
- _O_RAW constant
- translation constants
- _O_BINARY constant
- translation, constants
- translation, modes
- translation modes (file I/O)
ms.assetid: a5993bf4-7e7a-47f9-83c3-e46332b85579
ms.openlocfilehash: a86c0c1a0b70613c6e7749c78f58f6dfb3602d4d
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2019
ms.locfileid: "68376288"
---
# <a name="translation-mode-constants"></a>轉譯模式常數

## <a name="syntax"></a>語法

```
#include <fcntl.h>
```

## <a name="remarks"></a>備註

`_O_BINARY` 和 `_O_TEXT` 資訊清單常數判斷檔案的轉譯模式 (`_open` 和 `_sopen`) 或資料流的轉譯模式 (`_setmode`)。

允許的值包括：

|||
|-|-|
`_O_TEXT`  | 以文字 (已轉譯) 模式開啟檔案。 歸位字元–換行字元 (CR-LF) 的組合會在輸入中轉譯為單行換行 (LF)。 換行字元會在輸出中轉譯為 CR-LF 組合。 此外，Ctrl+Z 會在輸入中解譯成檔案結尾字元。 在為了讀取或讀取和寫入而開啟的檔案中，`fopen` 會儘可能檢查檔案結尾是否有 Ctrl+Z 並加以移除。 這樣做的原因是因為使用 `fseek` 和 `ftell` 函式在以 Ctrl+Z 結束的檔案內移動可能會讓 `fseek` 在檔案結尾附近產生不當行為。
`_O_BINARY`  | 以二進位 (未轉譯) 模式開啟檔案。 會隱藏上述轉譯。
`_O_RAW`  | 與 `_O_BINARY` 相同。 支援 C 2.0 相容性。

如需詳細資訊，請參閱[文字和二進位模式檔案 I/O](../c-runtime-library/text-and-binary-mode-file-i-o.md) 和[檔案轉譯](../c-runtime-library/file-translation-constants.md)。

## <a name="see-also"></a>另請參閱

[_open、_wopen](../c-runtime-library/reference/open-wopen.md)<br/>
[_pipe](../c-runtime-library/reference/pipe.md)<br/>
[_sopen、_wsopen](../c-runtime-library/reference/sopen-wsopen.md)<br/>
[_setmode](../c-runtime-library/reference/setmode.md)<br/>
[全域常數](../c-runtime-library/global-constants.md)

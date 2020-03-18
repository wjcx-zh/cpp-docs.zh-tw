---
title: 檔案讀取-寫入存取常數
ms.date: 11/04/2016
helpviewer_keywords:
- read/write access constants
- write access constants
- access constants for file read/write
- constants [C++], file attributes
- file read/write access constants
ms.assetid: 56cd1d22-39a5-4fcf-bea2-7046d249e8ee
ms.openlocfilehash: 96d146b2e2f0ed82cbdc52b11d92c049da50e2cb
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438388"
---
# <a name="file-readwrite-access-constants"></a>檔案讀取/寫入存取常數

## <a name="syntax"></a>語法

```
#include <stdio.h>
```

## <a name="remarks"></a>備註

這些常數會指定對檔案要求的存取類型 ("a"、"r" 或 "w")。 [轉譯模式](../c-runtime-library/file-translation-constants.md) ("b" 或 "t") 和[認可到磁碟模式](../c-runtime-library/commit-to-disk-constants.md) ("c" 或 "n") 都可以與存取類型一起指定。

存取類型如下表所述：

|存取類型|描述|
|----------|----------------|
|**"r"**|開啟以讀取。 如果檔案不存在或找不到，開啟檔案的呼叫就會失敗。|
|**"w"**|開啟空白檔案以寫入。 如果指定的檔案已存在，其內容將被終結。|
|**"a"**|開啟以寫入該檔案結尾 (附加)；如果該檔案不存在，便會先建立檔案。 所有的寫入作業都會在檔案結尾進行。 即使檔案指標可以使用 `fseek` 或 `rewind` 重新調整位置，但是在執行任何寫入作業之前，一律會移回至檔案結尾。 |
|**"r+"**|開啟以進行讀取和寫入。 如果檔案不存在或找不到，開啟檔案的呼叫就會失敗。|
|**"w+"**|開啟空白檔案以進行讀取和寫入。 如果指定的檔案已存在，其內容將被終結。|
|**"a+"**|與 **"a"** 相同，但也允許讀取。|

指定 "r+"、"w+"或 "a+" 類型時，會同時允許讀取和寫入 (表示檔案是要開啟以供「更新」之用)。 不過，當您在讀取和寫入之間切換時，必須有中間的 `fflush`、`fsetpos`、`fseek` 或 `rewind` 作業。 可以針對 `fsetpos` 或 `fseek` 作業指定目前位置。

## <a name="see-also"></a>另請參閱

[_fdopen、wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)<br/>
[fopen、_wfopen](../c-runtime-library/reference/fopen-wfopen.md)<br/>
[freopen、_wfreopen](../c-runtime-library/reference/freopen-wfreopen.md)<br/>
[_fsopen、_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)<br/>
[_popen、_wpopen](../c-runtime-library/reference/popen-wpopen.md)<br/>
[全域常數](../c-runtime-library/global-constants.md)

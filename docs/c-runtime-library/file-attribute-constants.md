---
title: 檔案屬性常數
ms.date: 11/04/2016
f1_keywords:
- A_HIDDEN
- _A_NORMAL
- _A_SUBDIR
- _A_RDONLY
- A_NORMAL
- A_SUBDIR
- _A_SYSTEM
- c.constants.file
- _A_HIDDEN
- A_RDONLY
- _A_ARCH
- A_ARCH
helpviewer_keywords:
- constants [C++], file attributes
- file attribute constants [C++]
- _A_SYSTEM constant
- files [C++], file attribute constants
- _A_SUBDIR constant
- _A_ARCH constant
- _A_NORMAL constant
- _A_HIDDEN constant
- _A_RDONLY constant
ms.assetid: 8dc8ccb9-99f5-446b-876c-7ebecc2f764f
ms.openlocfilehash: 271459c33cdcc1110222871bdca06d3f04edb497
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750880"
---
# <a name="file-attribute-constants"></a>檔案屬性常數

## <a name="syntax"></a>語法

```
#include <io.h>
```

## <a name="remarks"></a>備註

這些常數會指定函式所指定檔案或目錄的目前屬性。

屬性會由下列所示常數來代表：

|常數|說明|
|-|-|
|`_A_ARCH`| 封存。 每當 BACKUP 命令變更或清除檔案時即設定。 值：0x20|
|`_A_HIDDEN`| 隱藏的檔案。 除非您使用 /AH 選項，否則使用 DIR 命令時並不常見。 傳回一般檔案以及具有此屬性之檔案的相關資訊。 值：0x02|
|`_A_NORMAL`| 一般。 檔案可進行讀取或寫入而不受限制。 值：0x00|
|`_A_RDONLY`| 唯讀。 無法開啟檔案以進行寫入，也無法建立具有相同名稱的檔案。 值：0x01|
|`_A_SUBDIR`| 子目錄。 值：0x10|
|`_A_SYSTEM`| 系統檔案。 除非使用 /AS 選項，否則使用 DIR 命令時並不常見。 值：0x04|

可以使用 OR 運算子 (&#124;) 結合多個常數。

## <a name="see-also"></a>另請參閱

[檔案名稱搜尋函式](../c-runtime-library/filename-search-functions.md)<br/>
[全域常數](../c-runtime-library/global-constants.md)

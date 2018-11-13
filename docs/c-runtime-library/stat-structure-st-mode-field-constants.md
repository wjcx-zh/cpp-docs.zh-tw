---
title: _stat 結構 st_mode 欄位常數
ms.date: 11/04/2016
f1_keywords:
- S_IFCHR
- S_IFDIR
- _S_IWRITE
- S_IFMT
- _S_IFDIR
- _S_IREAD
- S_IEXEC
- _S_IEXEC
- _S_IFMT
- S_IWRITE
- S_IFREG
- S_IREAD
- _S_IFCHR
- _S_IFREG
helpviewer_keywords:
- S_IFDIR constant
- stat structure
- S_IWRITE constant
- S_IEXEC constant
- _S_IFREG constant
- S_IREAD constant
- stat structure, constants
- _S_IFMT constant
- st_mode field constants
- S_IFMT constant
- _S_IEXEC constant
- _S_IWRITE constant
- _S_IFDIR constant
- S_IFREG constant
- S_IFCHR constant
- _S_IREAD constant
- _S_IFCHR constant
ms.assetid: fd462004-7563-4766-8443-30b0a86174b6
ms.openlocfilehash: edb88c70a58c501ae09342c91b6c5ec667b8151c
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2018
ms.locfileid: "51523828"
---
# <a name="stat-structure-stmode-field-constants"></a>_stat 結構 st_mode 欄位常數

## <a name="syntax"></a>語法

```

#include <sys/stat.h>
```

## <a name="remarks"></a>備註

這些常數是用來表示 [_stat 結構](../c-runtime-library/standard-types.md)的 **st_mode** 欄位中的檔案類型。

位元遮罩常數如下所示：

|常數|意義|
|--------------|-------------|
|`_S_IFMT`|檔案類型遮罩|
|`_S_IFDIR`|Directory|
|`_S_IFCHR`|字元特殊 (設定時表示裝置)|
|`_S_IFREG`|Regular|
|`_S_IREAD`|讀取權限，擁有者|
|`_S_IWRITE`|寫入權限，擁有者|
|`_S_IEXEC`|執行/搜尋權限，擁有者|

## <a name="see-also"></a>請參閱

[_stat、_wstat 函式](../c-runtime-library/reference/stat-functions.md)<br/>
[_fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[標準類型](../c-runtime-library/standard-types.md)<br/>
[全域常數](../c-runtime-library/global-constants.md)
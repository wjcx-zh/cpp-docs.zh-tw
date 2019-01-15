---
title: 檔案使用權限常數
ms.date: 11/04/2016
f1_keywords:
- _S_IWRITE
- _S_IREAD
helpviewer_keywords:
- S_IWRITE constant
- constants [C++], file attributes
- S_IREAD constant
- file permissions [C++]
- _S_IWRITE constant
- _S_IREAD constant
ms.assetid: 593cad33-31d1-44d2-8941-8af7d210c88c
ms.openlocfilehash: c0c5e02458fa6b5436b029392a40bd2f54f22c0c
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220279"
---
# <a name="file-permission-constants"></a>檔案使用權限常數

## <a name="syntax"></a>語法

```
#include <sys/stat.h>
```

## <a name="remarks"></a>備註

當指定 `_O_CREAT` (`_open`,`_sopen`) 時，需要這些常數的其中之一。

`pmode` 引數會指定如下所示的檔案使用權限設定。

|常數|意義|
|--------------|-------------|
|`_S_IREAD`|允許讀取|
|`_S_IWRITE`|允許寫入|
|`_S_IREAD` &#124; `_S_IWRITE`|允許讀取和寫入|

作為 `_umask` 的 `pmode` 引數時，如下所示的常數會設定使用權限設定。

|常數|意義|
|--------------|-------------|
|`_S_IREAD`|不允許寫入 (檔案為唯讀)|
|`_S_IWRITE`|不允許讀取 (檔案為唯寫)|
|`_S_IREAD` &#124; `_S_IWRITE`|不允許讀取和寫入|

## <a name="see-also"></a>請參閱

[_open、_wopen](../c-runtime-library/reference/open-wopen.md)<br/>
[_sopen、_wsopen](../c-runtime-library/reference/sopen-wsopen.md)<br/>
[_umask](../c-runtime-library/reference/umask.md)<br/>
[標準類型](../c-runtime-library/standard-types.md)<br/>
[全域常數](../c-runtime-library/global-constants.md)

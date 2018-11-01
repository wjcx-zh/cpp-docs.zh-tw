---
title: _unlock_file
ms.date: 11/04/2016
apiname:
- _unlock_file
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _unlock_file
- unlock_file
helpviewer_keywords:
- files [C++], unlocking
- unlock_file function
- _unlock_file function
- unlocking files
ms.assetid: cf380a51-6d3a-4f38-bd64-2d4fb57b4369
ms.openlocfilehash: e3d11cbd59ef5846b33908ae6b6c40d7ea6125e8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552525"
---
# <a name="unlockfile"></a>_unlock_file

解除鎖定檔案，並允許其他處理序存取檔案。

## <a name="syntax"></a>語法

```C
void _unlock_file(
   FILE* file
);
```

### <a name="parameters"></a>參數

*file*<br/>
檔案控制代碼。

## <a name="remarks"></a>備註

**_Unlock_file**函式解除鎖定所指定的檔案*檔案*。 解除鎖定檔案可讓其他處理序存取檔案。 應該不會呼叫此函式，除非 **_lock_file**上呼叫過*檔案*指標。 呼叫 **_unlock_file**上不會遭到鎖定的檔案可能會導致死結。 如需範例，請參閱 [_lock_file](lock-file.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_unlock_file**|\<stdio.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[檔案處理](../../c-runtime-library/file-handling.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_lock_file](lock-file.md)<br/>

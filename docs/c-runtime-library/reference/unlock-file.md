---
title: _unlock_file
ms.date: 11/04/2016
api_name:
- _unlock_file
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _unlock_file
- unlock_file
helpviewer_keywords:
- files [C++], unlocking
- unlock_file function
- _unlock_file function
- unlocking files
ms.assetid: cf380a51-6d3a-4f38-bd64-2d4fb57b4369
ms.openlocfilehash: 2983408f066ea00c0b7ab111d9a6349700ecaece
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957482"
---
# <a name="_unlock_file"></a>_unlock_file

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

**_Unlock_file**函數會解除鎖定檔案所指定*的檔案。* 解除鎖定檔案可讓其他處理序存取檔案。 除非先前已在*檔案指標上*呼叫 **_lock_file** ，否則不應呼叫此函式。 在未鎖定的檔案上呼叫 **_unlock_file**可能會導致鎖死。 如需範例，請參閱 [_lock_file](lock-file.md)。

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

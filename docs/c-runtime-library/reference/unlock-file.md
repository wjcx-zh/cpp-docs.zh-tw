---
title: _unlock_file | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- files [C++], unlocking
- unlock_file function
- _unlock_file function
- unlocking files
ms.assetid: cf380a51-6d3a-4f38-bd64-2d4fb57b4369
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d000dce4c0009341c787a211ed8ef41d1728b51b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32407768"
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

*檔案*檔案控制代碼。

## <a name="remarks"></a>備註

**_Unlock_file**函式所指定的檔案會解除鎖定*檔案*。 解除鎖定檔案可讓其他處理序存取檔案。 此函式不應該呼叫除非 **_lock_file**之前已呼叫上*檔案*指標。 呼叫 **_unlock_file**不會遭到鎖定的檔案上可能會導致死結。 如需範例，請參閱 [_lock_file](lock-file.md)。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_unlock_file**|\<stdio.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[檔案處理](../../c-runtime-library/file-handling.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_lock_file](lock-file.md)<br/>

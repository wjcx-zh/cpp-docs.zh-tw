---
title: _commit | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _commit
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _commit
- commit
dev_langs:
- C++
helpviewer_keywords:
- files [C++], flushing
- flushing files to disk
- commit function
- _commit function
- committing files to disk
ms.assetid: d0c74d3a-4f2d-4fb0-b140-2d687db3d233
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3e9bc746c347bfb60fb78edbf025b676f8218c66
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="commit"></a>_commit

將檔案直接清除至磁碟。

## <a name="syntax"></a>語法

```C
int _commit(
   int fd
);
```

### <a name="parameters"></a>參數

*fd*<br/>
參照已開啟之檔案的檔案描述元。

## <a name="return-value"></a>傳回值

**_commit**傳回 0，如果檔案已成功排清至磁碟。 傳回值-1 表示錯誤。

## <a name="remarks"></a>備註

**_Commit**函式會強制寫入檔案與相關聯的作業系統*fd*至磁碟。 這個呼叫確保立即清除指定的檔案，而不是由作業系統自行決定。

如果*fd*是無效的檔案描述項無效參數處理常式會叫用中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，此函數會傳回-1 和**errno**設**EBADF**。

## <a name="requirements"></a>需求

|常式|必要的標頭|選擇性標頭|
|-------------|---------------------|----------------------|
|**_commit**|\<io.h>|\<errno.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[低層級 I/O](../../c-runtime-library/low-level-i-o.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_read](read.md)<br/>
[_write](write.md)<br/>

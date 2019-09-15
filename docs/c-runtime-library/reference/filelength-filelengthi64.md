---
title: _filelength、_filelengthi64
ms.date: 11/04/2016
api_name:
- _filelengthi64
- _filelength
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _filelength
- _filelengthi64
- filelengthi64
helpviewer_keywords:
- filelengthi64 function
- lengths, file
- filelength function
- _filelength function
- files [C++], length
- _filelengthi64 function
ms.assetid: 3ab83d5a-543c-4079-b9d9-0abfc7da0275
ms.openlocfilehash: d7cf7f5bea5ed8964ec1a714a2a70d289daf085f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957214"
---
# <a name="_filelength-_filelengthi64"></a>_filelength、_filelengthi64

取得檔案的長度。

## <a name="syntax"></a>語法

```C
long _filelength(
   int fd
);
__int64 _filelengthi64(
   int fd
);
```

### <a name="parameters"></a>參數

*fd*<br/>
檔案描述元的目標。

## <a name="return-value"></a>傳回值

**_Filelength**和 **_filelengthi64**都會傳回與*fd*相關聯之目標檔案的檔案長度（以位元組為單位）。 如果*fd*是不正確檔案描述項，則此函式會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這兩個函式會傳回-1L 來表示錯誤，並將**errno**設定為**EBADF**。

## <a name="requirements"></a>需求

|函數|必要的標頭|
|--------------|---------------------|
|**_filelength**|\<io.h>|
|**_filelengthi64**|\<io.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [_chsize](chsize.md) 的範例。

## <a name="see-also"></a>另請參閱

[檔案處理](../../c-runtime-library/file-handling.md)<br/>
[_chsize](chsize.md)<br/>
[_fileno](fileno.md)<br/>
[_fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_stat、_wstat 函式](stat-functions.md)<br/>

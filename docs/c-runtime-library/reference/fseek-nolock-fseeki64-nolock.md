---
title: _fseek_nolock、_fseeki64_nolock
ms.date: 11/04/2016
api_name:
- _fseek_nolock
- _fseeki64_nolock
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
- _fseek_nolock
- _fseeki64_nolock
- fseek_nolock
- fseeki64_nolock
helpviewer_keywords:
- _fseek_nolock function
- fseeki64_nolock function
- file pointers [C++], moving
- fseek_nolock function
- _fseeki64_nolock function
- seek file pointers
ms.assetid: 2dd4022e-b715-462b-b935-837561605a02
ms.openlocfilehash: c72f44b214893a6702f5da5594db7725a2f02136
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956533"
---
# <a name="_fseek_nolock-_fseeki64_nolock"></a>_fseek_nolock、_fseeki64_nolock

將檔案指標移至指定的位置。

## <a name="syntax"></a>語法

```C
int _fseek_nolock(
   FILE *stream,
   long offset,
   int origin
);
int _fseeki64_nolock(
   FILE *stream,
   __int64 offset,
   int origin
);
```

### <a name="parameters"></a>參數

*stream*<br/>
**FILE** 結構的指標。

*offset*<br/>
從 *origin* 位移的位元組數目。

*origin*<br/>
初始位置。

## <a name="return-value"></a>傳回值

分別與[fseek](fseek-fseeki64.md)和[_fseeki64](fseek-fseeki64.md)相同。

## <a name="remarks"></a>備註

這些函式分別是[fseek](fseek-fseeki64.md)和[_fseeki64](fseek-fseeki64.md)的非鎖定版本。 這些與[fseek](fseek-fseeki64.md)和[_fseeki64](fseek-fseeki64.md)相同，不同之處在于它們不受保護，不會受到其他執行緒的干擾。 這些函式因為不會造成鎖定其他執行緒的額外負荷，所以可能會比較快。 這些函式只能用在安全執行緒內容 (例如單一執行緒應用程式) 或呼叫範圍已經處理執行緒隔離的地方。

## <a name="requirements"></a>需求

|函數|必要的標頭|
|--------------|---------------------|
|**_fseek_nolock**、 **_fseeki64_nolock**|\<stdio.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[ftell、_ftelli64](ftell-ftelli64.md)<br/>
[_lseek、_lseeki64](lseek-lseeki64.md)<br/>
[rewind](rewind.md)<br/>

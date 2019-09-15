---
title: _ftell_nolock、_ftelli64_nolock
ms.date: 11/04/2016
api_name:
- _ftelli64_nolock
- _ftell_nolock
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
- _ftelli64_nolock
- ftelli64_nolock
- ftell_nolock
- _ftell_nolock
helpviewer_keywords:
- ftelli64_nolock function
- _ftelli64_nolock function
- _ftell_nolock function
- ftell_nolock function
- file pointers [C++], getting current position
ms.assetid: 84e68b0a-32f8-4c4a-90ad-3f2387685ede
ms.openlocfilehash: 9e72687077cc5401bb411fca81a3ccec48a6258f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956357"
---
# <a name="_ftell_nolock-_ftelli64_nolock"></a>_ftell_nolock、_ftelli64_nolock

取得檔案指標的目前位置，而不需要鎖定執行緒。

## <a name="syntax"></a>語法

```C
long _ftell_nolock(
   FILE *stream
);
__int64 _ftelli64_nolock(
   FILE *stream
);
```

### <a name="parameters"></a>參數

*stream*<br/>
以檔案**結構為**目標。

## <a name="return-value"></a>傳回值

與**ftell**和 **_ftelli64**相同。 如需詳細資訊，請參閱[ftell、_ftelli64](ftell-ftelli64.md)。

## <a name="remarks"></a>備註

這些函式分別為非鎖定版本的**ftell**和 **_ftelli64**。 它們與**ftell**和 **_ftelli64**相同，不同之處在于它們不受保護，不會受到其他執行緒的干擾。 這些函式因為不會造成鎖定其他執行緒的額外負荷，所以可能會比較快。 這些函式只能用在安全執行緒內容 (例如單一執行緒應用程式) 或呼叫範圍已經處理執行緒隔離的地方。

## <a name="requirements"></a>需求

|函數|必要的標頭|選擇性標頭|
|--------------|---------------------|---------------------|
|**ftell_nolock**|\<stdio.h>|\<errno.h>|
|**_ftelli64_nolock**|\<stdio.h>|\<errno.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fgetpos](fgetpos.md)<br/>
[fseek、_fseeki64](fseek-fseeki64.md)<br/>
[_lseek、_lseeki64](lseek-lseeki64.md)<br/>
[ftell、_ftelli64](ftell-ftelli64.md)<br/>

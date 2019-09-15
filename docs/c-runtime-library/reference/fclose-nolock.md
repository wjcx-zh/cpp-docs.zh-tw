---
title: _fclose_nolock
ms.date: 11/04/2016
api_name:
- _fclose_nolock
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
- fclose_nolock
- _fclose_nolock
helpviewer_keywords:
- streams, closing
- fclose_nolock function
- _fclose_nolock function
ms.assetid: b4af4392-5fc8-49bb-9fe2-ca7293d3ce04
ms.openlocfilehash: 2e19604f09cdb3ac2a5bfc1635c2b98a8d5218c5
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941420"
---
# <a name="_fclose_nolock"></a>_fclose_nolock

關閉資料流但不鎖定執行緒。

## <a name="syntax"></a>語法

```C
int _fclose_nolock(
   FILE *stream
);
```

### <a name="parameters"></a>參數

*stream*<br/>
**FILE** 結構的指標。

## <a name="return-value"></a>傳回值

如果成功關閉資料流程， **fclose**會傳回0。 傳回**EOF**表示錯誤。

## <a name="remarks"></a>備註

此函式是**fclose**的非鎖定版本。 完全一致，唯一不同在於不受保護，不能免於其他執行緒的干擾。 因為它不會造成鎖定其他執行緒的額外負荷，所以可能會比較快。 這個函式只能用在安全執行緒內容 (例如單一執行緒應用程式) 或呼叫範圍已經處理執行緒隔離的地方。

## <a name="requirements"></a>需求

|函數|必要的標頭|
|--------------|---------------------|
|**_fclose_nolock**|\<stdio.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_close](close.md)<br/>
[_fdopen、wfdopen](fdopen-wfdopen.md)<br/>
[fflush](fflush.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
f[reopen、_wfreopen](freopen-wfreopen.md)<br/>

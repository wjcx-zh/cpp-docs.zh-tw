---
title: _ftell_nolock、_ftelli64_nolock
ms.date: 4/2/2020
api_name:
- _ftelli64_nolock
- _ftell_nolock
- _o__ftell_nolock
- _o__ftelli64_nolock
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 9f1f0018773f8fb5b00f1304011ba8128ce7d9df
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910000"
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

*資料流*<br/>
以檔案**結構為**目標。

## <a name="return-value"></a>傳回值

與**ftell**和 **_ftelli64**相同。 如需詳細資訊，請參閱[ftell、_ftelli64](ftell-ftelli64.md)。

## <a name="remarks"></a>備註

這些函式分別是**ftell**和 **_ftelli64**的非鎖定版本。 它們與**ftell**和 **_ftelli64**相同，不同之處在于它們不受保護，不會受到其他執行緒的干擾。 這些函式因為不會造成鎖定其他執行緒的額外負荷，所以可能會比較快。 這些函式只能用在安全執行緒內容 (例如單一執行緒應用程式) 或呼叫範圍已經處理執行緒隔離的地方。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|函式|必要的標頭|選擇性標頭|
|--------------|---------------------|---------------------|
|**ftell_nolock**|\<stdio.h>|\<errno.h>|
|**_ftelli64_nolock**|\<stdio.h>|\<errno.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fgetpos](fgetpos.md)<br/>
[fseek、_fseeki64](fseek-fseeki64.md)<br/>
[_lseek、_lseeki64](lseek-lseeki64.md)<br/>
[ftell、_ftelli64](ftell-ftelli64.md)<br/>

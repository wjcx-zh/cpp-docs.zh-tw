---
title: _ftell_nolock、_ftelli64_nolock | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _ftelli64_nolock
- _ftell_nolock
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
- _ftelli64_nolock
- ftelli64_nolock
- ftell_nolock
- _ftell_nolock
dev_langs:
- C++
helpviewer_keywords:
- ftelli64_nolock function
- _ftelli64_nolock function
- _ftell_nolock function
- ftell_nolock function
- file pointers [C++], getting current position
ms.assetid: 84e68b0a-32f8-4c4a-90ad-3f2387685ede
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f00920fbb262cd564ce0ac6bc454d3ef560c6941
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="ftellnolock-ftelli64nolock"></a>_ftell_nolock、_ftelli64_nolock

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
目標**檔案**結構。

## <a name="return-value"></a>傳回值

與相同**ftell**和 **_ftelli64**。 如需詳細資訊，請參閱[ftell、 _ftelli64](ftell-ftelli64.md)。

## <a name="remarks"></a>備註

這些函式是非鎖定版本**ftell**和 **_ftelli64**分別。 它們是相同**ftell**和 **_ftelli64**不同之處在於它們未受保護的干擾由其他執行緒。 這些函式因為不會造成鎖定其他執行緒的額外負荷，所以可能會比較快。 這些函式只能用在安全執行緒內容 (例如單一執行緒應用程式) 或呼叫範圍已經處理執行緒隔離的地方。

## <a name="requirements"></a>需求

|功能|必要的標頭|選擇性標頭|
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

---
title: _fwrite_nolock | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _fwrite_nolock
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
- _fwrite_nolock
- fwrite_nolock
dev_langs:
- C++
helpviewer_keywords:
- fwrite_nolock function
- streams, writing data to
- _fwrite_nolock function
ms.assetid: 2b4ec6ce-742e-4615-8407-44a0a18ec1d7
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 03e04dd884b4b96f64a4d4ece5b61fe5aeafb3a1
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="fwritenolock"></a>_fwrite_nolock

將資料寫入資料流，而不需要鎖定執行緒。

## <a name="syntax"></a>語法

```C
size_t _fwrite_nolock(
   const void *buffer,
   size_t size,
   size_t count,
   FILE *stream
);
```

### <a name="parameters"></a>參數

*buffer*<br/>
要寫入之資料的指標。

*size*<br/>
項目大小 (位元組)。

*count*<br/>
要寫入之項目的最大數量。

*資料流*<br/>
**FILE** 結構的指標。

## <a name="return-value"></a>傳回值

與 [fwrite](fwrite.md) 相同。

## <a name="remarks"></a>備註

此函式為非鎖定版本**fwrite**。 它相當於**fwrite**不同之處在於它不受干擾其他執行緒。 因為它不會造成鎖定其他執行緒的額外負荷，所以可能會比較快。 這個函式只能用在安全執行緒內容 (例如單一執行緒應用程式) 或呼叫範圍已經處理執行緒隔離的地方。

## <a name="requirements"></a>需求

|功能|必要的標頭|
|--------------|---------------------|
|**_fwrite_nolock**|\<stdio.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [fread](fread.md) 的範例。

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fread](fread.md)<br/>
[_write](write.md)<br/>

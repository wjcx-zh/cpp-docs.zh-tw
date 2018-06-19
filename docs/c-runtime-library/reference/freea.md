---
title: _freea | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _freea
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
apitype: DLLExport
f1_keywords:
- freea
- _freea
dev_langs:
- C++
helpviewer_keywords:
- _freea function
- freea function
- memory deallocation
ms.assetid: dcd30584-dd9d-443b-8c4c-13237a1cecac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8ac01f965e159dae19bbbd748c1692058063a211
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32403599"
---
# <a name="freea"></a>_freea

取消配置或釋放記憶體區塊。

## <a name="syntax"></a>語法

```C
void _freea(
   void *memblock
);
```

### <a name="parameters"></a>參數

*memblock*<br/>
要釋放之先前配置的記憶體區塊。

## <a name="return-value"></a>傳回值

無。

## <a name="remarks"></a>備註

**_Freea**函式會取消配置的記憶體區塊 (*memblock*) 先前呼叫所配置的[_malloca](malloca.md)。 **_freea**檢查堆積或堆疊上是否已配置的記憶體。 如果是在堆疊配置 **_freea**不做任何動作。 如果配置於堆積，所釋放的位元組數目相當於配置區塊時所要求的位元組數目。 如果*memblock*是**NULL**，指標就會忽略和 **_freea**立即傳回。 嘗試釋放指標無效 (未配置的記憶體區塊的指標 **_malloca**) 可能會影響後續的配置要求，而且會發生錯誤。

**_freea**呼叫**可用**內部如果找到，在堆積上配置記憶體。 記憶體在堆積還是堆疊上取決於在記憶體之已配置記憶體正前方的位址所放置的標記。

如果發生錯誤時即釋放記憶體， **errno**設為從作業系統在本質上失敗的資訊。 如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

釋放記憶體區塊之後，[_heapmin](heapmin.md) 會聯合未使用的區域並將它們釋放回作業系統，以將堆積上的可用記憶體數量降到最低。 未釋放給作業系統的已釋放記憶體會還原到可用集區，並且再度可供重新配置。

呼叫 **_freea**必須隨附的所有呼叫 **_malloca**。 它也會發生的錯誤呼叫 **_freea**兩次是在相同的記憶體。 C 執行階段程式庫的偵錯版本連結應用程式是時，特別是使用[_malloc_dbg](malloc-dbg.md)定義啟用的功能 **_CRTDBG_MAP_ALLOC**，更輕鬆地尋找遺失或重複呼叫 **_freea**。 如需如何在偵錯程序期間管理堆積的詳細資訊，請參閱 [CRT 偵錯堆積](/visualstudio/debugger/crt-debug-heap-details)。

**_freea**標示`__declspec(noalias)`，這表示，此函式保證不會修改全域變數。 如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md)。

## <a name="requirements"></a>需求

|功能|必要的標頭|
|--------------|---------------------|
|**_freea**|\<stdlib.h> 和 \<malloc.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [_malloca](malloca.md) 的範例。

## <a name="see-also"></a>另請參閱

[記憶體配置](../../c-runtime-library/memory-allocation.md)<br/>
[_malloca](malloca.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
[realloc](realloc.md)<br/>
[_free_dbg](free-dbg.md)<br/>
[_heapmin](heapmin.md)<br/>

---
title: 任意
ms.date: 11/04/2016
api_name:
- free
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
- api-ms-win-crt-heap-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- free
helpviewer_keywords:
- memory blocks, deallocating
- free function
ms.assetid: 74ded9cf-1863-432e-9306-327a42080bb8
ms.openlocfilehash: 7e09bec7c83eae64064e3997f2e8d5632a47258a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956720"
---
# <a name="free"></a>任意

取消配置或釋放記憶體區塊。

## <a name="syntax"></a>語法

```C
void free(
   void *memblock
);
```

### <a name="parameters"></a>參數

*memblock*<br/>
要釋放之先前配置的記憶體區塊。

## <a name="remarks"></a>備註

**Free**函式會解除配置先前由**calloc**、 **malloc**或**realloc**的呼叫所配置的記憶體區塊（*memblock*）。 已釋放的位元組數目相當於配置區塊時所要求的位元組數（如果是**realloc**，則會重新配置）。 如果*memblock*為**Null**，則會忽略指標，而**free**會立即傳回。 嘗試釋放無效指標（不是由**calloc**、 **malloc**或**realloc**所配置之記憶體區塊的指標）可能會影響後續配置要求，並導致錯誤。

如果釋放記憶體時發生錯誤，則會在失敗的本質中，使用作業系統的資訊來設定**errno** 。 如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

釋放記憶體區塊之後，[_heapmin](heapmin.md) 會聯合未使用的區域並將它們釋放回作業系統，以將堆積上的可用記憶體數量降到最低。 未釋放給作業系統的已釋放記憶體會還原到可用集區，並且再度可供重新配置。

當應用程式與 C 執行時間程式庫的 debug 版本連結時， **free**會解析為[_free_dbg](free-dbg.md)。 如需如何在偵錯程序期間管理堆積的詳細資訊，請參閱 [CRT 偵錯堆積](/visualstudio/debugger/crt-debug-heap-details)。

**free**已標記`__declspec(noalias)`為，表示保證不會修改全域變數。 如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md)。

若要釋放使用 [_malloca](malloca.md) 所配置的記憶體，請使用 [_freea](freea.md)。

## <a name="requirements"></a>需求

|函數|必要的標頭|
|--------------|---------------------|
|**free**|\<stdlib.h> 和 \<malloc.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [malloc](malloc.md) 的範例。

## <a name="see-also"></a>另請參閱

[記憶體配置](../../c-runtime-library/memory-allocation.md)<br/>
[_alloca](alloca.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
[_free_dbg](free-dbg.md)<br/>
[_heapmin](heapmin.md)<br/>
[_freea](freea.md)<br/>

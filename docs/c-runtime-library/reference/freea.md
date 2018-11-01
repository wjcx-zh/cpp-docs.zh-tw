---
title: _freea
ms.date: 11/04/2016
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
helpviewer_keywords:
- _freea function
- freea function
- memory deallocation
ms.assetid: dcd30584-dd9d-443b-8c4c-13237a1cecac
ms.openlocfilehash: ac9c5528755898b0de131bccf94185b501b0e720
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605890"
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

**_Freea**函式會取消配置記憶體區塊 (*memblock*) 的先前呼叫所配置[_malloca](malloca.md)。 **_freea**檢查以查看 是否堆積或堆疊上配置的記憶體。 如果配置於堆疊 **_freea**不執行任何動作。 如果配置於堆積，所釋放的位元組數目相當於配置區塊時所要求的位元組數目。 如果*memblock*是**NULL**，會忽略指標，並 **_freea**立即傳回。 嘗試釋放無效指標 (未配置之記憶體區塊指標 **_malloca**) 可能會影響後續配置要求，並導致錯誤。

**_freea**呼叫**免費**內部如果找到，在堆積上配置記憶體時，才。 記憶體在堆積還是堆疊上取決於在記憶體之已配置記憶體正前方的位址所放置的標記。

如果發生錯誤時釋放記憶體**errno**資訊從作業系統在本質上失敗的設定。 如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

釋放記憶體區塊之後，[_heapmin](heapmin.md) 會聯合未使用的區域並將它們釋放回作業系統，以將堆積上的可用記憶體數量降到最低。 未釋放給作業系統的已釋放記憶體會還原到可用集區，並且再度可供重新配置。

呼叫 **_freea**必須伴隨所有呼叫 **_malloca**。 它也會呼叫錯誤 **_freea**兩次是在相同的記憶體。 當應用程式連結偵錯版的 C 執行階段程式庫中，特別是使用[_malloc_dbg](malloc-dbg.md)所定義的功能 **_CRTDBG_MAP_ALLOC**，更輕鬆地尋找遺失或重複呼叫 **_freea**。 如需如何在偵錯程序期間管理堆積的詳細資訊，請參閱 [CRT 偵錯堆積](/visualstudio/debugger/crt-debug-heap-details)。

**_freea**標示`__declspec(noalias)`，這表示保證函式時，會不能修改全域變數。 如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md)。

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

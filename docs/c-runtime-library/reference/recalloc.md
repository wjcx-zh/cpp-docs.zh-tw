---
title: _recalloc
ms.date: 4/2/2020
api_name:
- _recalloc
- _o__recalloc
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _recalloc
- recalloc
helpviewer_keywords:
- _recalloc function
- recalloc function
ms.assetid: 1db8305a-3f03-418c-8844-bf9149f63046
ms.openlocfilehash: 57972a48336d8dd362b5da7513c854703134921b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338115"
---
# <a name="_recalloc"></a>_recalloc

**真實和****卡洛克**的組合。 重新配置記憶體中的陣列，並將其項目初始化為 0。

## <a name="syntax"></a>語法

```C
void *_recalloc(
   void *memblock
   size_t num,
   size_t size
);
```

### <a name="parameters"></a>參數

*memblock*<br/>
先前配置之記憶體區塊的指標。

*數量*<br/>
項目數。

*大小*<br/>
每個項目的長度 (位元組)。

## <a name="return-value"></a>傳回值

**_recalloc**返回指向重新分配(並可能移動)記憶體塊**的空**指標。

如果沒有足夠的可用記憶體將塊擴展到給定的大小,則原始塊保持不變,並且**返回 NULL。**

如果請求的大小為零,則釋放*memblock*指向的塊;如果請求的大小為零。"返回值為**NULL***NULL,memblock*被保留在已釋放的塊上。

儲存空間的傳回值指標，是能夠適當地對齊任何物件類型之儲存區的保證。 要取得指向**void**以外的類型的指標,請使用返回值上強制轉換的類型。

## <a name="remarks"></a>備註

**_recalloc**函數更改已分配記憶體區塊的大小。 *memblock*參數指向記憶體塊的開頭。 如果*memblock*為**NULL,****則_recalloc**與[calloc](calloc.md)相同的方式,並分配一個新的*編號* * *大小*位元組塊。 每個項目都會初始化為 0。 如果*memblock*不是**NULL,** 它應該是前一個調用 call 傳回的指向**calloc、malloc**或[realloc](malloc.md)的指標。 [realloc](realloc.md)

由於新塊可以位於新的記憶體位置,因此 **_recalloc**返回的指標不能保證是通過*memblock*參數傳遞的指標。

**_recalloc**如果記憶體分配失敗或請求的記憶體量超過 **_HEAP_MAXREQ,** 則將**errno**設置到**ENOMEM。** 如需此錯誤碼和其他錯誤碼的資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

**recalloc**調用**realloc**以使用[C++_set_new_mode](set-new-mode.md)函數來設置新的處理程式模式。 新的處理程式模式指示**realloc**在發生故障時是否調用[由 _set_new_handler](set-new-handler.md)設置的新處理程式例程。 默認情況下 **,Realloc**不會在分配記憶體失敗時調用新的處理程式例程。 您可以重寫此預設行為,以便在 **_recalloc**無法分配記憶體時 **,Realloc**調用新處理程式例程的方式**與新運算符出於**相同原因失敗時相同。 若要覆寫預設值，請及早在程式中呼叫

```C
_set_new_mode(1);
```

或與 NEWMODE.OBJ 連結。

當應用程式連結到 C 執行時庫的除錯版本時 **,_recalloc**解析為[_recalloc_dbg](recalloc-dbg.md)。 如需如何在偵錯程序期間管理堆積的詳細資訊，請參閱 [CRT 偵錯堆積](/visualstudio/debugger/crt-debug-heap-details)。

**_recalloc**標記`__declspec(noalias)`為`__declspec(restrict)`, 表示保證函數不修改全域變數,並且返回的指標不會別名。 如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md) 和 [restrict](../../cpp/restrict.md)。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_recalloc**|\<stdlib.h> 和 \<malloc.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[記憶體配置](../../c-runtime-library/memory-allocation.md)<br/>
[_recalloc_dbg](recalloc-dbg.md)<br/>
[_aligned_recalloc](aligned-recalloc.md)<br/>
[_aligned_offset_recalloc](aligned-offset-recalloc.md)<br/>
[自由](free.md)<br/>
[連結選項](../../c-runtime-library/link-options.md)<br/>

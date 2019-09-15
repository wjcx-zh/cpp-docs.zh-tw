---
title: _recalloc
ms.date: 11/04/2016
api_name:
- _recalloc
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
- _recalloc
- recalloc
helpviewer_keywords:
- _recalloc function
- recalloc function
ms.assetid: 1db8305a-3f03-418c-8844-bf9149f63046
ms.openlocfilehash: f06631fe4dd0abcb0b18895ccb04e5b52cda6a2c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949452"
---
# <a name="_recalloc"></a>_recalloc

**Realloc**和**calloc**的組合。 重新配置記憶體中的陣列，並將其項目初始化為 0。

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

*number*<br/>
項目數。

*size*<br/>
每個項目的長度 (位元組)。

## <a name="return-value"></a>傳回值

**_recalloc**會傳回已重新配置（且可能已移動）記憶體區塊的**void**指標。

如果沒有足夠的可用記憶體可將區塊展開為指定的大小，原始區塊會保留不變，而且會傳回**Null** 。

如果要求的大小為零，則會釋放*memblock*所指向的區塊;傳回值為**Null**，而*memblock*是指向釋放的區塊。

儲存空間的傳回值指標，是能夠適當地對齊任何物件類型之儲存區的保證。 若要取得**void**以外類型的指標，請在傳回值上使用類型轉換。

## <a name="remarks"></a>備註

**_Recalloc**函數會變更已配置記憶體區塊的大小。 *Memblock*引數會指向記憶體區塊的開頭。 如果*memblock*為**Null**， **_recalloc**的行為會與[calloc](calloc.md)相同，並會配置新的*數位* * *大小*位元組區塊。 每個元素都會初始化為 0。 如果*memblock*不是**Null**，它應該是先前對**calloc**、 [malloc](malloc.md)或[realloc](realloc.md)的呼叫所傳回的指標。

由於新的區塊可以在新的記憶體位置中，因此 **_recalloc**所傳回的指標不一定是透過*memblock*引數傳遞的指標。

如果記憶體配置失敗，或所要求的記憶體數量超過 **_HEAP_MAXREQ**，則 **_recalloc**會將**errno**設定為**ENOMEM** 。 如需此錯誤碼和其他錯誤碼的資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

**recalloc**會呼叫**realloc** ，以便使用C++ [_set_new_mode](set-new-mode.md)函數來設定新的處理常式模式。 新的處理常式模式指出，在失敗時， **realloc**是否會呼叫[_set_new_handler](set-new-handler.md)所設定的新處理常式常式。 根據預設， **realloc**不會在失敗時呼叫新的處理常式常式來配置記憶體。 您可以覆寫此預設行為，如此一來，當 **_recalloc**無法配置記憶體時， **realloc**會呼叫新的處理常式常式，就像**新**的運算子因為相同的原因而失敗。 若要覆寫預設值，請及早在程式中呼叫

```C
_set_new_mode(1);
```

或與 NEWMODE.OBJ 連結。

當應用程式與 C 執行時間程式庫的 debug 版本連結時， **_recalloc**會解析為[_recalloc_dbg](recalloc-dbg.md)。 如需如何在偵錯程序期間管理堆積的詳細資訊，請參閱 [CRT 偵錯堆積](/visualstudio/debugger/crt-debug-heap-details)。

**_recalloc**標示`__declspec(noalias)`為和`__declspec(restrict)`，表示保證函式不會修改全域變數，而且傳回的指標沒有別名。 如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md) 和 [restrict](../../cpp/restrict.md)。

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
[free](free.md)<br/>
[連結選項](../../c-runtime-library/link-options.md)<br/>

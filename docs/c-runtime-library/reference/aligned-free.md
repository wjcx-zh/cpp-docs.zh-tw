---
title: _aligned_free
ms.date: 4/2/2020
api_name:
- _aligned_free
- _o__aligned_free
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
- aligned_free
- _aligned_free
helpviewer_keywords:
- _aligned_free function
- aligned_free function
ms.assetid: ed1ce952-cdfc-4682-85cc-f75d4101603d
ms.openlocfilehash: a6e5f0dcd0bbea436ecdad7abb1fd6fc948f80dc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350708"
---
# <a name="_aligned_free"></a>_aligned_free

釋放使用 [_aligned_malloc](aligned-malloc.md) 或 [_aligned_offset_malloc](aligned-offset-malloc.md) 所配置的記憶體區塊。

## <a name="syntax"></a>語法

```C
void _aligned_free (
   void *memblock
);
```

### <a name="parameters"></a>參數

*memblock*<br/>
傳回 `_aligned_malloc` 或 `_aligned_offset_malloc` 函式之記憶體區塊的指標。

## <a name="remarks"></a>備註

**_aligned_free**被標`__declspec(noalias)`記 ,這意味著保證函數不修改全域變數。 如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md)。

不同於其他 _aligned CRT 函式，此函式不會驗證其參數。 如果*memblock*是 NULL 指標,則此函數僅執行任何操作。 它不會變更 `errno` 也不會叫用無效的參數處理常式。 如果因為之前未使用 _aligned 函式配置記憶體區塊致使函式發生錯誤，或因為某些無法預見的不幸致使記憶體發生不一致，函式會從 [_RPT、_RPTF、_RPTW、_RPTFW 巨集](rpt-rptf-rptw-rptfw-macros.md)產生偵錯報告。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_aligned_free**|\<malloc.h>|

## <a name="example"></a>範例

如需詳細資訊，請參閱 [_aligned_malloc](aligned-malloc.md)。

## <a name="see-also"></a>另請參閱

[資料對齊](../../c-runtime-library/data-alignment.md)

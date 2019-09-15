---
title: _aligned_free
ms.date: 11/04/2016
api_name:
- _aligned_free
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
- aligned_free
- _aligned_free
helpviewer_keywords:
- _aligned_free function
- aligned_free function
ms.assetid: ed1ce952-cdfc-4682-85cc-f75d4101603d
ms.openlocfilehash: 44556d3f044a567f4903ef14a4b2a9b353af02ff
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943976"
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

**_aligned_free**標示`__declspec(noalias)`為，表示保證函式不會修改全域變數。 如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md)。

不同於其他 _aligned CRT 函式，此函式不會驗證其參數。 如果*memblock*為 Null 指標，則此函式只會執行任何動作。 它不會變更 `errno` 也不會叫用無效的參數處理常式。 如果因為之前未使用 _aligned 函式配置記憶體區塊致使函式發生錯誤，或因為某些無法預見的不幸致使記憶體發生不一致，函式會從 [_RPT、_RPTF、_RPTW、_RPTFW 巨集](rpt-rptf-rptw-rptfw-macros.md)產生偵錯報告。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_aligned_free**|\<malloc.h>|

## <a name="example"></a>範例

如需詳細資訊，請參閱 [_aligned_malloc](aligned-malloc.md)。

## <a name="see-also"></a>另請參閱

[資料對齊](../../c-runtime-library/data-alignment.md)
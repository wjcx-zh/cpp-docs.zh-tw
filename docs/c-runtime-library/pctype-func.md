---
title: __pctype_func
ms.date: 4/2/2020
api_name:
- __pctype_func
- _o___pctype_func
api_location:
- msvcrt.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr80.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __pctype_func
helpviewer_keywords:
- __pctype_func
ms.assetid: d52b8add-d07d-4516-a22f-e836cde0c57f
ms.openlocfilehash: a7972744d322cf16d056f70fff83f529a183020e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213641"
---
# <a name="__pctype_func"></a>__pctype_func

擷取字元分類資訊陣列的指標。

## <a name="syntax"></a>語法

```cpp
const unsigned short *__pctype_func(
   )
```

## <a name="return-value"></a>傳回值

字元分類資訊陣列的指標。

## <a name="remarks"></a>備註

「字元分類」資料表中的資訊僅供內部使用，供分類類型為之字元的各種函式使用 **`char`** 。 如需詳細資訊，請參閱 [_pctype、_pwctype、_wctype、_mbctype、_mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md) 的 `Remarks` 節。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|__pctype_func|ctype.h|

## <a name="see-also"></a>另請參閱

[_pctype、_pwctype、_wctype、_mbctype、_mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md)

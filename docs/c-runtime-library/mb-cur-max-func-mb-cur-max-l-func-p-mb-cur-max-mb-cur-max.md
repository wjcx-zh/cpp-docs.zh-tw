---
title: ___mb_cur_max_func、___mb_cur_max_l_func、__p___mb_cur_max、__mb_cur_max
ms.date: 4/2/2020
api_name:
- ___mb_cur_max_l_func
- __p___mb_cur_max
- ___mb_cur_max_func
- __mb_cur_max
- _o____mb_cur_max_func
api_location:
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
- msvcr100.dll
- msvcrt.dll
- msvcr90.dll
- msvcr120.dll
- api-ms-win-crt-locale-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- ___mb_cur_max_func
- ___mb_cur_max_l_func
- __p___mb_cur_max
- __mb_cur_max
helpviewer_keywords:
- __mb_cur_max
- ___mb_cur_max_func
- ___mb_cur_max_l_func
- __p___mb_cur_max
ms.assetid: 60d36108-1ca7-45a6-8ce7-68a91f13e3a1
ms.openlocfilehash: f9b9e2d903bb05f5b1b653b4fb51c57b354d4126
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351084"
---
# <a name="___mb_cur_max_func-___mb_cur_max_l_func-__p___mb_cur_max-__mb_cur_max"></a>___mb_cur_max_func、___mb_cur_max_l_func、__p___mb_cur_max、__mb_cur_max

內部 CRT 函式。 以多位元組字元為單位，擷取目前或指定之地區設定的最大位元組數目。

## <a name="syntax"></a>語法

```cpp
int ___mb_cur_max_func(void);
int ___mb_cur_max_l_func(_locale_t locale);
int * __p___mb_cur_max(void);
#define __mb_cur_max (___mb_cur_max_func())
```

#### <a name="parameters"></a>參數

地區設定用於擷取結果的地區設定結構。 若此值為 null，則會使用目前執行緒地區設定。

## <a name="return-value"></a>傳回值

目前或指定之地區設定的最大位元組數目 (以多位元組字元為單位)。

## <a name="remarks"></a>備註

這是 CRT 用於從執行緒區域儲存區擷取 [MB_CUR_MAX](../c-runtime-library/mb-cur-max.md) 巨集之目前值的內部函式。 建議您為了可攜性在程式碼中使用 `MB_CUR_MAX` 巨集。

`__mb_cur_max` 巨集是呼叫 `___mb_cur_max_func()` 函式的便利方式。 `__p___mb_cur_max` 函式是針對與 Visual C++ 5.0 及更新版本的相容性所定義。

內部 CRT 函式是特別針對實作，且會依每個版本而有所不同。 不建議將此函式用於您的程式碼中。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|`___mb_cur_max_func`, `___mb_cur_max_l_func`, `__p___mb_cur_max`|\<ctype.h>、\<stdlib.h>|

## <a name="see-also"></a>另請參閱

[MB_CUR_MAX](../c-runtime-library/mb-cur-max.md)

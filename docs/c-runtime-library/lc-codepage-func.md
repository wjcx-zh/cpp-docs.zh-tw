---
title: ___lc_codepage_func
ms.date: 4/2/2020
api_name:
- ___lc_codepage_func
- _o____lc_codepage_func
api_location:
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcr100.dll
- msvcr90.dll
- msvcr110.dll
- msvcrt.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- lc_codepage_func
- ___lc_codepage_func
helpviewer_keywords:
- ___lc_codepage_func
ms.assetid: 6a663bd0-5a63-4a2f-9507-872ec1582aae
ms.openlocfilehash: 2f3eeb4611a0a41ff1782e0b162cd65d86d3ef65
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351239"
---
# <a name="___lc_codepage_func"></a>___lc_codepage_func

內部 CRT 函式。 擷取執行緒的目前字碼頁。

## <a name="syntax"></a>語法

```cpp
UINT ___lc_codepage_func(void);
```

## <a name="return-value"></a>傳回值

執行緒的目前字碼頁。

## <a name="remarks"></a>備註

`___lc_codepage_func` 是內部 CRT 函式，由其他 CRT 函式用於從 CRT 資料的執行緒區域儲存區取得目前的字碼頁。 也可以使用 [_get_current_locale](../c-runtime-library/reference/get-current-locale.md) 函式來取得此資訊。

「字碼頁」** 是單一位元組或雙位元組字碼和個別字元之間的對應。 不同的字碼頁包含不同的特殊字元，一般而言是針對語言或語言群組進行自訂。 如需字碼頁的詳細資訊，請參閱 [Code Pages](../c-runtime-library/code-pages.md)。

內部 CRT 函式是特別針對實作，且會依每個版本而有所不同。 不建議將此函式用於您的程式碼中。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|`___lc_codepage_func`|crt\src\setlocal.h|

## <a name="see-also"></a>另請參閱

[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)<br/>
[setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale、_wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)<br/>
[_free_locale](../c-runtime-library/reference/free-locale.md)

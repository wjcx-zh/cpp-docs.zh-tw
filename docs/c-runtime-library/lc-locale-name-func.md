---
title: ___lc_locale_name_func
ms.date: 11/04/2016
apiname:
- ___lc_locale_name_func
apilocation:
- msvcrt.dll
- msvcr110.dll
- msvcr100.dll
- msvcr90.dll
- msvcr120.dll
- msvcr80.dll
- msvcr110_clr0400.dll
apitype: DLLExport
f1_keywords:
- ___lc_locale_name_func
helpviewer_keywords:
- ___lc_locale_name_func
ms.assetid: ef858308-872e-43de-95e0-9b1b4084343e
ms.openlocfilehash: 88ce07ca3fece558c23f4fcd9a12949f184b7532
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57741050"
---
# <a name="lclocalenamefunc"></a>___lc_locale_name_func

內部 CRT 函式。 擷取執行緒的目前地區設定名稱。

## <a name="syntax"></a>語法

```cpp
wchar_t** ___lc_locale_name_func(void);
```

## <a name="return-value"></a>傳回值

包含執行緒的目前地區設定名稱之字串的指標。

## <a name="remarks"></a>備註

`___lc_locale_name_func` 是內部 CRT 函式，由其他 CRT 函式用於從 CRT 資料的執行緒區域儲存區取得目前的地區設定。 也可以使用 [_get_current_locale](../c-runtime-library/reference/get-current-locale.md) 函式或 [setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) 函式來取得此資訊。

內部 CRT 函式是特別針對實作，且會依每個版本而有所不同。 不建議將此函式用於您的程式碼中。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|`___lc_locale_name_func`|crt\src\setlocal.h|

## <a name="see-also"></a>另請參閱

[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)<br/>
[setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale、_wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)<br/>
[_free_locale](../c-runtime-library/reference/free-locale.md)

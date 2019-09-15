---
title: ___lc_collate_cp_func
ms.date: 11/04/2016
api_name:
- ___lc_collate_cp_func
api_location:
- msvcr120.dll
- msvcrt.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr90.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- ___lc_collate_cp_func
helpviewer_keywords:
- ___lc_collate_cp_func
ms.assetid: 46ccc084-7ac9-4e5d-9138-e12cb5845615
ms.openlocfilehash: d6a857760bf3b76481cc608ef8f015bca207f35f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940146"
---
# <a name="___lc_collate_cp_func"></a>___lc_collate_cp_func

內部 CRT 函式。 擷取執行緒的目前定序字碼頁。

## <a name="syntax"></a>語法

```cpp
UINT ___lc_codepage_func(void);
```

## <a name="return-value"></a>傳回值

執行緒的目前定序字碼頁。

## <a name="remarks"></a>備註

`___lc_collate_cp_func` 是內部 CRT 函式，由其他 CRT 函式用於從 CRT 資料的執行緒區域儲存區取得目前的定序字碼頁。 也可以使用 [_get_current_locale](../c-runtime-library/reference/get-current-locale.md) 函式來取得此資訊。

內部 CRT 函式是特別針對實作，且會依每個版本而有所不同。 不建議將此函式用於您的程式碼中。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|`___lc_collate_cp_func`|crt\src\setlocal.h|

## <a name="see-also"></a>另請參閱

[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)<br/>
[setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale、_wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)<br/>
[_free_locale](../c-runtime-library/reference/free-locale.md)

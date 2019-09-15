---
title: _set_controlfp
ms.date: 04/05/2018
api_name:
- _set_controlfp
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_controlfp
- _set_controlfp
helpviewer_keywords:
- set_controlfp function
- floating-point functions, setting control word
- _set_controlfp function
ms.assetid: e0689d50-f68a-4028-a9c1-fb23eedee4ad
ms.openlocfilehash: 4d39406db0f4c9ba6374776da62aea2dbb61e23d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948676"
---
# <a name="_set_controlfp"></a>_set_controlfp

設定浮點控制字組。

## <a name="syntax"></a>語法

```C
void __cdecl _set_controlfp(
    unsigned int newControl,
    unsigned int mask
);
```

### <a name="parameters"></a>參數

*newControl*<br/>
新的控制字組位元值。

*mask*<br/>
要設定之新控制字組位元的遮罩。

## <a name="return-value"></a>傳回值

無。

## <a name="remarks"></a>備註

**_Set_controlfp**函數類似于 **_control87**，但它只會將浮點控制字組設定為*newControl*。 值中的位元表示浮點控制狀態。 浮點控制狀態可讓程式變更浮點數學套件中的精確度、四捨五入和無限大模式。 您也可以使用 **_set_controlfp**來遮罩或取消遮罩浮點例外狀況。 如需詳細資訊，請參閱 [_control87、_controlfp、\__control87_2](control87-controlfp-control87-2.md)。

使用[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)進行編譯時，此函式已被取代，因為 Common language runtime 只支援預設的浮點精確度。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|相容性|
|-------------|---------------------|-------------------|
|**_set_controlfp**|\<float.h>|僅限 x86 處理器|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[_clear87、_clearfp](clear87-clearfp.md)<br/>
[_status87、_statusfp、_statusfp2](status87-statusfp-statusfp2.md)<br/>

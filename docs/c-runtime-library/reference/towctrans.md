---
title: towctrans
ms.date: 11/04/2016
api_name:
- towctrans
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
- api-ms-win-crt-string-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- towctrans
helpviewer_keywords:
- towctrans function
ms.assetid: 1ed1e70d-7b31-490f-a7d9-42564b5924ca
ms.openlocfilehash: d63fc343647cd0f949f282e2a64d4a0636e62bd7
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957431"
---
# <a name="towctrans"></a>towctrans

轉換字元。

## <a name="syntax"></a>語法

```C
wint_t towctrans(
   wint_t c,
   wctrans_t category
);
```

### <a name="parameters"></a>參數

*C*<br/>
您想要轉換的字元。

*category*<br/>
識別碼，包含 [wctrans](wctrans.md) 的傳回值。

## <a name="return-value"></a>傳回值

**Towctrans**在*類別*中使用轉換規則之後的字元*c*。

## <a name="remarks"></a>備註

先前成功呼叫[wctrans](wctrans.md)時，必須傳回*category*的值。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**towctrans**|\<wctype.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

如需使用**towctrans**的範例，請參閱**wctrans** 。

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>

---
title: _mbbtombc、_mbbtombc_l
ms.date: 11/04/2016
api_name:
- _mbbtombc_l
- _mbbtombc
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
- api-ms-win-crt-multibyte-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbbtombc_l
- _mbbtombc
- mbbtombc_l
- mbbtombc
helpviewer_keywords:
- mbbtombc_l function
- mbbtombc function
- _mbbtombc_l function
- _mbbtombc function
ms.assetid: 78593389-b0fc-43b6-8c1f-2a6bf702d64e
ms.openlocfilehash: 244e603a3234b755d19a1c1d0738e8c22d74b8e2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952741"
---
# <a name="_mbbtombc-_mbbtombc_l"></a>_mbbtombc、_mbbtombc_l

將單一位元組的多位元組字元轉換成對應之雙位元組的多位元組字元。

> [!IMPORTANT]
> 這個應用程式開發介面不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
unsigned int _mbbtombc(
   unsigned int c
);
unsigned int _mbbtombc_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*C*<br/>
要轉換的單一位元組字元。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

如果 **_mbbtombc**成功轉換*c*，則會傳回多位元組字元;否則，它會傳回*c*。

## <a name="remarks"></a>備註

**_Mbbtombc**函數會將指定的單一位元組多位元組字元轉換成對應的雙位元組多位元組字元。 字元必須在 0x20-0x7E 或 0xA1-0xDF 的範圍內，才能進行轉換。

輸出值會受到地區設定的**LC_CTYPE**分類設定影響;如需詳細資訊，請參閱[setlocale、_wsetlocale](setlocale-wsetlocale.md) 。 這個函式的版本完全相同，不同之處在于 **_mbbtombc**會針對此地區設定相關的行為使用目前的地區設定，而 **_mbbtombc_l**則改用傳入的地區設定參數。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

在舊版中， **_mbbtombc**的名稱為**hantozen**。 針對新的程式碼，請使用 **_mbbtombc**。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_mbbtombc**|\<mbstring.h>|
|**_mbbtombc_l**|\<mbstring.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[_mbctombb、_mbctombb_l](mbctombb-mbctombb-l.md)<br/>

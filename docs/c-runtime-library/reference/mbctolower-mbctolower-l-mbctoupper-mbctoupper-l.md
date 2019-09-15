---
title: _mbctolower、_mbctolower_l、_mbctoupper、_mbctoupper_l
ms.date: 11/04/2016
api_name:
- _mbctolower_l
- _mbctoupper_l
- _mbctoupper
- _mbctolower
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
- mbctoupper_l
- mbctolower_l
- _mbctolower
- _mbctolower_l
- _mbctoupper
- mbctoupper
- mbctolower
- _mbctoupper_l
helpviewer_keywords:
- _mbctolower function
- mbctolower_l function
- totupper function
- _mbctoupper function
- totlower function
- _mbctoupper_l function
- mbctolower function
- _totupper function
- _mbctolower_l function
- mbctoupper_l function
- _totlower function
- mbctoupper function
ms.assetid: 787fab71-3224-4ed7-bc93-4dcd8023fc54
ms.openlocfilehash: 75b3926ea294fd6fe66b4e6865ac0c7df6d1b596
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952545"
---
# <a name="_mbctolower-_mbctolower_l-_mbctoupper-_mbctoupper_l"></a>_mbctolower、_mbctolower_l、_mbctoupper、_mbctoupper_l

測試並轉換多位元組字元的大小寫。

> [!IMPORTANT]
> 這個應用程式開發介面不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
unsigned int _mbctolower(
   unsigned int c
);
unsigned int _mbctolower_l(
   unsigned int c,
   _locale_t locale
);
unsigned int _mbctoupper(
   unsigned int c
);
unsigned int _mbctoupper_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*C*<br/>
要轉換的多位元組字元。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

所有這些函式都會傳回轉換的字元*c*（如果可能的話）。 否則，它會傳回未變更的字元*c* 。

## <a name="remarks"></a>備註

函式會測試字元*c* ，並在可能的情況下套用下列其中一個轉換。

|常式|轉換|
|--------------|--------------|
|**_mbctolower**、 **_mbctolower_l**|將大寫字元轉換為小寫字元。|
|**_mbctoupper**、 **_mbctoupper_l**|將小寫字元轉換為大寫字元。|

輸出值會受到地區設定的 **LC_CTYPE** 分類設定影響；如需詳細資訊，請參閱 [setlocale](setlocale-wsetlocale.md)。 此函式的版本若沒有 **_l**尾碼，會針對此地區設定相關的行為使用目前的地區設定;具有 **_l**尾碼的版本相同，不同之處在于它會改為使用傳入的地區設定參數。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

在先前版本中， **_mbctolower**稱為**jtolower**，而 **_mbctoupper**稱為**jtoupper**。 對於新的程式碼，請改用新名稱。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_totlower**|**tolower**|**_mbctolower**|**towlower**|
|**_totlower_l**|**_tolower_l**|**_mbctolower_l**|**_towlower_t**|
|**_totupper**|**toupper**|**_mbctoupper**|**towupper**|
|**_totupper_l**|**toupper_l**|**_mbctoupper_l**|**_towupper_l**|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|--------------|---------------------|
|**_mbctolower**、 **_mbctolower_l**|\<mbstring.h>|
|**_mbctoupper**、 **_mbctoupper_l**|\<mbstring.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[_mbbtombc、_mbbtombc_l](mbbtombc-mbbtombc-l.md)<br/>
[_mbcjistojms、_mbcjistojms_l、_mbcjmstojis、_mbcjmstojis_l](mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)<br/>
[_mbctohira、_mbctohira_l、_mbctokata、_mbctokata_l](mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)<br/>
[_mbctombb、_mbctombb_l](mbctombb-mbctombb-l.md)<br/>

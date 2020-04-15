---
title: _mbsnbicmp、_mbsnbicmp_l
ms.date: 4/2/2020
api_name:
- _mbsnbicmp_l
- _mbsnbicmp
- _o__mbsnbicmp
- _o__mbsnbicmp_l
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbsnbicmp
- mbsnbicmp
- mbsnbicmp_l
- _mbsnbicmp_l
helpviewer_keywords:
- _tcsnicmp_l function
- _strnicmp function
- mbsnbicmp_l function
- _wcsnicmp_l function
- _mbsnbicmp function
- _mbsnbicmp_l function
- _tcsnicmp function
- _strnicmp_l function
- mbsnbicmp function
- _wcsnicmp function
ms.assetid: ddb44974-8b0c-42f0-90d0-56c9350bae0c
ms.openlocfilehash: 80d2708396cdaeb86c25932c3d13129fb318719a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340569"
---
# <a name="_mbsnbicmp-_mbsnbicmp_l"></a>_mbsnbicmp、_mbsnbicmp_l

比較兩個多位元位元串的**n**位元組,並忽略大小寫。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
int _mbsnbicmp(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
```

### <a name="parameters"></a>參數

*字串1*,*字串2*<br/>
以 Null 結束的待比較字串。

*count*<br/>
要比較的位元組數目。

## <a name="return-value"></a>傳回值

傳回值表示子字串之間的關聯性。

|傳回值|描述|
|------------------|-----------------|
|< 0|*字串 1*子字串小於*string2*子字串。|
|0|*字串1*子字串與*string2*子字串相同。|
|> 0|*字串1*子字串大於*string2*子字串。|

在錯誤時 **,_mbsnbicmp**返回 **_NLSCMPERROR**,在 String.h 和 Mbstring.h 中定義。

## <a name="remarks"></a>備註

**_mbsnbicmp**函數最多執行*string1*和*string2*的第一個*計數位*的位級比較。 通過將每個字元轉換為小寫來執行比較;[_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md)是 **_mbsnbicmp**區分大小寫的版本。 如果在比較*計數*字元之前在任一字串中到達終止空字元,則比較結束。 如果在比較*計數*字元之前在任一字串中到達終止空字元時,字串相等,則較短的字串較小。

**_mbsnbicmp**與[_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md)類似,只是它將字串向上比較為*計數*位元組而不是按字元。

包含 ASCII 資料表中介於 'Z' 和 'a' 之間字元 ('['、'\\'、']'、'^'、'_' 和 '\`') 的兩個字串，會根據其大小寫以不同的方式進行比較。 例如,如果比較小寫("abcde">"abcd")和"ABCDE"<"ABCD_")是大寫,則兩個字串"ABCDE"和"ABCD+"比較一種方法。

**_mbsnbicmp**根據當前使用的[多位元組代碼頁](../../c-runtime-library/code-pages.md)識別多位元組字串序列。 不受目前地區設定的影響。

如果*string1*或*string2*是空指標 **,_mbsnbicmp**調用參數[驗證](../../c-runtime-library/parameter-validation.md)中所述的無效參數處理程式。 如果允許繼續執行,則函數將**傳回_NLSCMPERROR**並將**errno**設定到**EINVAL**。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnicmp**|**_strnicmp**|**_mbsnbicmp**|**_wcsnicmp**|
|**_tcsnicmp_l**|**_strnicmp_l**|**_mbsnbicmp_l**|**_wcsnicmp_l**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_mbsnbicmp**|\<mbstring.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [_mbsnbcmp、_mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md) 的範例。

## <a name="see-also"></a>另請參閱

[字串動作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat、_mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp、_mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_stricmp、_wcsicmp、_mbsicmp、_stricmp_l、_wcsicmp_l、_mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>

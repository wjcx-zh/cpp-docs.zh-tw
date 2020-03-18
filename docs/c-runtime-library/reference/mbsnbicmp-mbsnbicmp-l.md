---
title: _mbsnbicmp、_mbsnbicmp_l
ms.date: 11/04/2016
api_name:
- _mbsnbicmp_l
- _mbsnbicmp
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
ms.openlocfilehash: c7a4d5def115101c9f3fbd6c53d649ab5b122f1c
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442831"
---
# <a name="_mbsnbicmp-_mbsnbicmp_l"></a>_mbsnbicmp、_mbsnbicmp_l

比較兩個多位元組字元字串的**n**個位元組，並忽略大小寫。

> [!IMPORTANT]
> 這個應用程式開發介面不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
int _mbsnbicmp(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
```

### <a name="parameters"></a>參數

*string1*、 *string2*<br/>
以 Null 結束的待比較字串。

*計數*<br/>
要比較的位元組數目。

## <a name="return-value"></a>傳回值

傳回值表示子字串之間的關聯性。

|傳回值|描述|
|------------------|-----------------|
|< 0|小於*string2*子字串的*string1*子字串。|
|0|*string1*子字串與*string2*子字串相同。|
|> 0|大於*string2*子字串的*string1*子字串。|

發生錯誤時， **_mbsnbicmp**會傳回 **_NLSCMPERROR**，其定義在字串 .h 和 g. 中。

## <a name="remarks"></a>備註

**_Mbsnbicmp**函數最多可執行*string1*和*string2*的第一個*計數*位元組的序數比較。 比較是藉由將每個字元轉換成小寫來執行;[_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md)是 **_mbsnbicmp**的區分大小寫版本。 如果在比較*count*個字元之前，在任一字串中達到終止的 null 字元，則會結束比較。 如果字串在比較*計數*字元之前的任一字串中到達結束的 null 字元時相等，則較短的字串會較小。

**_mbsnbicmp**類似[_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md)，不同之處在于它會將字串與*計數*位元組（而非字元）進行比較。

包含 ASCII 資料表中介於 'Z' 和 'a' 之間字元 ('['、'\\'、']'、'^'、'_' 和 '\`') 的兩個字串，會根據其大小寫以不同的方式進行比較。 例如，如果比較為小寫（"ABCDE" > "abcd ^"），則兩個字串 "ABCDE" 和 "ABCD ^" 會比較一種方式，如果是大寫，則會另一種方式（"ABCDE" < "ABCD ^"）。

**_mbsnbicmp**會根據目前使用中的[多位元組字碼頁](../../c-runtime-library/code-pages.md)，辨識多位元組字元序列。 不受目前地區設定的影響。

如果*string1*或*string2*是 null 指標， **_mbsnbicmp**會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，此函式會傳回 **_NLSCMPERROR** ，並將**Errno**設定為**EINVAL**。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnicmp**|**_strnicmp**|**_mbsnbicmp**|**_wcsnicmp**|
|**_tcsnicmp_l**|**_strnicmp_l**|**_mbsnbicmp_l**|**_wcsnicmp_l**|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_mbsnbicmp**|\<mbstring.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [_mbsnbcmp、_mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md) 的範例。

## <a name="see-also"></a>另請參閱

[字串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat、_mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp、_mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_stricmp、_wcsicmp、_mbsicmp、_stricmp_l、_wcsicmp_l、_mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>

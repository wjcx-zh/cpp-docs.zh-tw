---
title: _mbsnbicmp、_mbsnbicmp_l
ms.date: 11/04/2016
apiname:
- _mbsnbicmp_l
- _mbsnbicmp
apilocation:
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
apitype: DLLExport
f1_keywords:
- _strnicmp
- _wcsnicmp_l
- _mbsnbicmp
- mbsnbicmp
- mbsnbicmp_l
- _tcsnicmp
- _strnicmp_l
- _tcsnicmp_l
- _wcsnicmp
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
ms.openlocfilehash: 059d0781e465f6491f27fd634bbc4479104bc12f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331294"
---
# <a name="mbsnbicmp-mbsnbicmpl"></a>_mbsnbicmp、_mbsnbicmp_l

比較**n**個位元組的兩個多位元組字元字串，並忽略大小寫。

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

*string1*， *string2*<br/>
以 Null 結束的待比較字串。

*count*<br/>
要比較的位元組數目。

## <a name="return-value"></a>傳回值

傳回值表示子字串之間的關聯性。

|傳回值|描述|
|------------------|-----------------|
|< 0|*string1*子字串小於*string2*子字串。|
|0|*string1*子字串等於*string2*子字串。|
|> 0|*string1*子字串大於*string2*子字串。|

發生錯誤時， **_mbsnbicmp**會傳回 **_NLSCMPERROR**，其定義於 String.h 和 Mbstring.h。

## <a name="remarks"></a>備註

**_Mbsnbicmp**函式會執行序數比較最多的第一個*計數*位元組*string1*並*string2*。 轉換為小寫; 每個字元來執行比較[_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md)區分大小寫版本 **_mbsnbicmp**。 如果達到結束的 null 字元之前任一字串中結束的比較*計數*來比較字元。 如果字串相等時結束的 null 字元，便到達之前任一字串中*計數*來比較字元、 短的字串為較小者。

**_mbsnbicmp**大致[_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md)，差異在於比較字串最多*計數*而不是由字元的位元組。

包含 ASCII 資料表中介於 'Z' 和 'a' 之間字元 ('['、'\\'、']'、'^'、'_' 和 '\`') 的兩個字串，會根據其大小寫以不同的方式進行比較。 例如，兩個字串"ABCDE"和"ABCD ^"比較其中一個方法，如果該比較為小寫 ("abcde">"abcd ^") 以及的其他方式 ("ABCDE"<"ABCD ^") 如果它是大寫。

**_mbsnbicmp**辨識多位元組字元序列，根據[多位元組字碼頁](../../c-runtime-library/code-pages.md)目前使用中。 不受目前地區設定的影響。

如果有任一*string1*或是*string2*為 null 指標， **_mbsnbicmp**叫用無效參數處理常式，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md). 如果允許繼續執行，則函數會傳回 **_NLSCMPERROR**並設定**errno**來**EINVAL**。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnicmp**|**_strnicmp**|**_mbsnbicmp**|**_wcsnicmp**|
|**_tcsnicmp_l**|**_strnicmp_l**|**_mbsnbicmp_l**|**_wcsnicmp_l**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
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

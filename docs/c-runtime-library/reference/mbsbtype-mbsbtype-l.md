---
title: _mbsbtype、_mbsbtype_l
ms.date: 4/2/2020
api_name:
- _mbsbtype_l
- _mbsbtype
- _o__mbsbtype
- _o__mbsbtype_l
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
- mbsbtype
- mbsbtype_l
- _mbsbtype_l
- _mbsbtype
helpviewer_keywords:
- _mbsbtype function
- mbsbtype function
- _mbsbtype_l function
- mbsbtype_l function
ms.assetid: 0d5dd91a-d32d-4f98-ac57-98dfc9e98eac
ms.openlocfilehash: d71a061d9af5028c9bc6b4008f9904606a233592
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340879"
---
# <a name="_mbsbtype-_mbsbtype_l"></a>_mbsbtype、_mbsbtype_l

傳回字串中的位元組類型。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
int _mbsbtype(
   const unsigned char *mbstr,
   size_t count
);
int _mbsbtype_l(
   const unsigned char *mbstr,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*姆布斯特*<br/>
多位元組字元序列的位址。

*count*<br/>
從字串開頭的位元組位移。

*現場*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

**_mbsbtype****和_mbsbtype_l**返回一個整數值,指示指定位元組上的測試結果。 下表中的資訊清單常數定義於 Mbctype.h。

|傳回值|位元組類型|
|------------------|---------------|
|**_MBC_SINGLE** (0)|單一位元組字元。 例如,在代碼頁 932 中,如果指定的位元組在 0x20 - 0x7E 或 0xA1 - 0xDF 範圍內 **,_mbsbtype**返回 0。|
|**_MBC_LEAD** (1)|多位元組字元的前導位元組。 例如,在代碼頁 932 中,如果指定的位元組在 0x81 - 0x9F 或 0xE0 - 0xFC 範圍內 **,_mbsbtype**返回 1。|
|**_MBC_TRAIL** (2)|多位元組字元的後隨位元組。 例如,在代碼頁 932 中,如果指定的位元組在 0x40 - 0x7E 或 0x80 - 0xFC 範圍內 **,_mbsbtype**返回 2。|
|**_MBC_ILLEGAL** (-1)|**在**位移*計數**(mbstr)* 的位元組之前找到的 NULL 字串、無效字元或空位元組。|

## <a name="remarks"></a>備註

**_mbsbtype**函數確定多位元位元串中的位元組類型。 函數僅檢查偏移*計數**(mbstr)* 的位元組,忽略指定位元組之前的無效字元。

輸出值會受到地區設定的 **LC_CTYPE** 分類設定影響；如需詳細資訊，請參閱 [setlocale](setlocale-wsetlocale.md)。 沒有 **_l**後置碼的函數版本使用此與區域設置相關的行為的當前區域設置;具有 **_l**後綴的版本是相同的,只不過它使用傳入區域設置參數。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

如果輸入字串為**NULL,** 則呼叫無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行 **,errno**將設定為**EINVAL,** 函數傳回 **_MBC_ILLEGAL**。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_mbsbtype**|\<mbstring.h>|\<mbctype.h>*|
|**_mbsbtype_l**|\<mbstring.h>|\<mbctype.h>*|

\* 適用於作為傳回值使用的資訊清單常數。

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[位元組分類](../../c-runtime-library/byte-classification.md)<br/>

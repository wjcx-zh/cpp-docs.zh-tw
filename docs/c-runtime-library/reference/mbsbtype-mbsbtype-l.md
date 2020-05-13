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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: c1431a2d0886ffd3d16b43abf82b7342c166273a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82909477"
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

*mbstr*<br/>
多位元組字元序列的位址。

*計數*<br/>
從字串開頭的位元組位移。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

**_mbsbtype**和 **_mbsbtype_l**會傳回一個整數值，指出指定位元組上的測試結果。 下表中的資訊清單常數定義於 Mbctype.h。

|傳回值|位元組類型|
|------------------|---------------|
|**_MBC_SINGLE** （0）|單一位元組字元。 例如，在字碼頁932中，如果指定的位元組在 0x20-0x7E 或 0xA1-0xDF 範圍內， **_mbsbtype**會傳回0。|
|**_MBC_LEAD** （1）|多位元組字元的前導位元組。 例如，在字碼頁932中，如果指定的位元組在 0x81-0x9F 或0xE0 的範圍內， **_mbsbtype**會傳回1。|
|**_MBC_TRAIL** （2）|多位元組字元的後隨位元組。 例如，在字碼頁932中，如果指定的位元組在 0x40-0x7E 或 0x80-0xFC 範圍內， **_mbsbtype**會傳回2。|
|**_MBC_ILLEGAL** （-1）|在*mbstr*中位移*計數*的位元組之前找到**null**字串、不正確字元或 null 位元組。|

## <a name="remarks"></a>備註

**_Mbsbtype**函式會判斷多位元組字元字串中的位元組類型。 函式只會檢查*mbstr*中位移*計數*的位元組，並忽略指定位元組之前的無效字元。

輸出值會受到地區設定的 **LC_CTYPE** 分類設定影響；如需詳細資訊，請參閱 [setlocale](setlocale-wsetlocale.md)。 此函式的版本若沒有 **_l**尾碼，會針對此地區設定相關的行為使用目前的地區設定;具有 **_l**尾碼的版本相同，不同之處在于它會改用傳入的地區設定參數。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

如果輸入字串是**Null**，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行， **errno**會設為**EINVAL** ，而函數會傳回 **_MBC_ILLEGAL**。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_mbsbtype**|\<mbstring.h>|\<mbctype.h>*|
|**_mbsbtype_l**|\<mbstring.h>|\<mbctype.h>*|

\* 適用於作為傳回值使用的資訊清單常數。

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[位元組分類](../../c-runtime-library/byte-classification.md)<br/>

---
title: _mbctombb、_mbctombb_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _mbctombb_l
- _mbctombb
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
- _mbctombb_l
- _mbctombb
- mbctombb_l
- mbctombb
dev_langs:
- C++
helpviewer_keywords:
- _mbctombb function
- mbctombb_l function
- mbctombb function
- _mbctombb_l function
ms.assetid: d90970b8-71ff-4586-b6a2-f9ceb811f776
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: adb233b489b5f4c190a4015805b07ab36770a283
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32402900"
---
# <a name="mbctombb-mbctombbl"></a>_mbctombb、_mbctombb_l

將雙位元組的多位元組字元轉換成對應之單一位元組的多位元組字元。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
unsigned int _mbctombb(
   unsigned int c
);
unsigned int _mbctombb_l(
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

如果成功的話， **_mbctombb**和 **_mbctombb_l**傳回對應至單一位元組字元*c*; 否則它會傳回*c*.

## <a name="remarks"></a>備註

**_Mbctombb**和 **_mbctombb_l**函式會將指定的多位元組字元轉換成對應的單一位元組多位元組字元。 字元必須對應到 0x20-0x7E 或 0xA1-範圍內的單一位元組字元轉換 0xDF。

輸出值會受到地區設定的 **LC_CTYPE** 分類設定影響；如需詳細資訊，請參閱 [setlocale](setlocale-wsetlocale.md)。 這個函數，而不需要的版本 **_l**後置詞會針對地區設定相關行為; 使用目前的地區設定的版本與 **_l**尾碼是完全相同，不同之處在於它會使用傳入的地區設定參數中改用。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

在舊版中， **_mbctombb**呼叫**zentohan**。 使用 **_mbctombb**改為。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_mbctombb**|\<mbstring.h>|
|**_mbctombb_l**|\<mbstring.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[_mbbtombc、_mbbtombc_l](mbbtombc-mbbtombc-l.md)<br/>
[_mbcjistojms、_mbcjistojms_l、_mbcjmstojis、_mbcjmstojis_l](mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)<br/>
[_mbctohira、_mbctohira_l、_mbctokata、_mbctokata_l](mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)<br/>
[_mbctolower、_mbctolower_l、_mbctoupper、_mbctoupper_l](mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)<br/>

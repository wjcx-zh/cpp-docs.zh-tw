---
title: _mbbtombc、_mbbtombc_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _mbbtombc_l
- _mbbtombc
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
- _mbbtombc_l
- _mbbtombc
- mbbtombc_l
- mbbtombc
dev_langs:
- C++
helpviewer_keywords:
- mbbtombc_l function
- mbbtombc function
- _mbbtombc_l function
- _mbbtombc function
ms.assetid: 78593389-b0fc-43b6-8c1f-2a6bf702d64e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 98053437d2e189c26b46b53ec34ef67740d62bce
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="mbbtombc-mbbtombcl"></a>_mbbtombc、_mbbtombc_l

將單一位元組的多位元組字元轉換成對應之雙位元組的多位元組字元。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

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

如果 **_mbbtombc**將成功轉換*c*，則會傳回多位元組字元; 否則它會傳回*c*。

## <a name="remarks"></a>備註

**_Mbbtombc**函式會將給定的單一位元組多位元組字元轉換成對應之雙位元組多位元組字元。 字元必須是介於 0x20-0x7E 或 0xA1-要轉換的 0xDF。

輸出值會影響的設定**LC_CTYPE**之地區設定分類設定，請參閱 < [setlocale、 _wsetlocale](setlocale-wsetlocale.md)如需詳細資訊。 此函式版本是一樣的不同之處在於 **_mbbtombc**會針對地區設定相關行為使用目前的地區設定和 **_mbbtombc_l**改為使用傳入的地區設定參數。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

在舊版中， **_mbbtombc**命名為**hantozen**。 對於新的程式碼， **_mbbtombc**。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_mbbtombc**|\<mbstring.h>|
|**_mbbtombc_l**|\<mbstring.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[_mbctombb、_mbctombb_l](mbctombb-mbctombb-l.md)<br/>

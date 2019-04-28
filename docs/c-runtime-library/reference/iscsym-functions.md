---
title: iscsym、iscsymf、__iscsym、__iswcsym、__iscsymf、__iswcsymf、_iscsym_l、_iswcsym_l、_iscsymf_l、_iswcsymf_l
ms.date: 11/04/2016
apiname:
- _iswcsym_l
- __iswcsym
- __iscsym
- _iswcsymf_l
- _iscsym_l
- __iswcsymf
- __iscsymf
- _iscsymf_l
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _iswcsym_l
- _iswcsymf_l
- iscsymf
- iswcsymf
- __iswcsym
- __iswcsymf
- iscsym
- iswcsym
- __iscsym
- _iscsym_l
- _iscsymf_l
- __iscsymf
- ctype/iscsym
- ctype/iscsymf
- ctype/__iscsym
- ctype/__iscsymf
- ctype/__iscsym_l
- ctype/__iscsymf_l
- ctype/__iswcsym
- ctype/__iswcsymf
- ctype/__iswcsym_l
- ctype/__iswcsymf_l
helpviewer_keywords:
- iscsymf_l function
- iswsym_l function
- _iswcsym_l function
- iscsym_l function
- _iscsymf_l function
- _iswcsymf_l function
- _iscsym_l function
- __iscsym function
- __iswcsymf function
- iswsymf_l function
- __iscsymf function
- __iswcsym function
- iscsym function
- iscsymf function
ms.assetid: 944dfb99-f2b8-498c-9f55-dbcf370d0a2c
ms.openlocfilehash: 8ee84243b98c08504ac0bb63593e39c32230b706
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331632"
---
# <a name="iscsym-iscsymf-iscsym-iswcsym-iscsymf-iswcsymf-iscsyml-iswcsyml-iscsymfl-iswcsymfl"></a>iscsym、iscsymf、__iscsym、__iswcsym、__iscsymf、__iswcsymf、_iscsym_l、_iswcsym_l、_iscsymf_l、_iswcsymf_l

判斷整數是否代表可用於識別項中的字元。

## <a name="syntax"></a>語法

```C
int __iscsym(
   int c
);
int __iswcsym(
   wint_t c
);
int __iscsymf(
   int c
);
int __iswcsymf(
   wint_t c
);
int _iscsym_l(
   int c,
   _locale_t locale
);
int _iswcsym_l(
   wint_t c,
   _locale_t locale
);
int _iscsymf_l(
   int c,
   _locale_t locale
);
int _iswcsymf_l(
   wint_t c,
   _locale_t locale
);
#define iscsym __iscsym
#define iscsymf __iscsymf
```

### <a name="parameters"></a>參數

*C*<br/>
待測試整數。 *c*應在 0-255 函式的窄字元版本的範圍內。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

兩者 **__iscsym**並 **__iswcsym**傳回非零值，如果*c*是字母、 底線或數字。 兩者 **__iscsymf**並 **__iswcsymf**傳回非零值，如果*c*是字母或底線。 這些常式都會傳回 0，如果*c*不符合測試條件。 使用這些函式的版本 **_l**後置詞都相同，只不過它們*地區設定*傳入而不是目前的地區設定的地區設定相關行為。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

## <a name="remarks"></a>備註

除非已定義前置處理器巨集 _CTYPE_DISABLE_MACROS，否則這些常式會被定義為巨集。 當您使用這些常式的巨集版本時，引數可多次評估。 您使用在引數清單中具有副作用的運算式時，請務必小心。

回溯相容性， **iscsym**並**iscsymf**定義為巨集時，才[ &#95; &#95;STDC&#95; &#95; ](../../preprocessor/predefined-macros.md)未定義或定義為 0;否則，其為未定義。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**iscsym**， **iscsymf**， **__iscsym**， **__iswcsym**， **__iscsymf**， **__iswcsymf**， **_iscsym_l**， **_iswcsym_l**， **_iscsymf_l**， **_iswcsymf_l**|C: \<ctype.h><br /><br /> C++: \<cctype> 或 \<ctype.h>|

**Iscsym**， **iscsymf**， **__iscsym**， **__iswcsym**， **__iscsymf**， **__iswcsymf**， **_iscsym_l**， **_iswcsym_l**， **_iscsymf_l**，並 **_iswcsymf_l**常式Microsoft 專有的。 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[字元分類](../../c-runtime-library/character-classification.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[is、isw 常式](../../c-runtime-library/is-isw-routines.md)<br/>

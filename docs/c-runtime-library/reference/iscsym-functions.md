---
title: iscsym、iscsymf、__iscsym、__iswcsym、__iscsymf、__iswcsymf、_iscsym_l、_iswcsym_l、_iscsymf_l、_iswcsymf_l
ms.date: 11/04/2016
api_name:
- _iswcsym_l
- __iswcsym
- __iscsym
- _iswcsymf_l
- _iscsym_l
- __iswcsymf
- __iscsymf
- _iscsymf_l
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
- api-ms-win-crt-string-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: ef5b2487fb49739f9a073adbc87546fb5d49d542
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954418"
---
# <a name="iscsym-iscsymf-__iscsym-__iswcsym-__iscsymf-__iswcsymf-_iscsym_l-_iswcsym_l-_iscsymf_l-_iswcsymf_l"></a>iscsym、iscsymf、__iscsym、__iswcsym、__iscsymf、__iswcsymf、_iscsym_l、_iswcsym_l、_iscsymf_l、_iswcsymf_l

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
待測試整數。 針對函式的窄字元版本， *c*應該在0-255 的範圍內。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

如果*c*是字母、底線或數位， **__iscsym**和 **__iswcsym**都會傳回非零值。 如果*c*是字母或底線， **__iscsymf**和 **__iswcsymf**都會傳回非零值。 如果*c*不符合測試條件，這些常式都會傳回0。 這些具有 **_l**尾碼的函式版本都相同，不同之處在于它們會使用傳入的*地區*設定，而非目前的地區設定來處理其地區設定相關的行為。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

## <a name="remarks"></a>備註

除非已定義前置處理器巨集 _CTYPE_DISABLE_MACROS，否則這些常式會被定義為巨集。 當您使用這些常式的巨集版本時，引數可多次評估。 您使用在引數清單中具有副作用的運算式時，請務必小心。

針對回溯相容性，只有在未定義[ &#95; &#95; &#95; STDC](../../preprocessor/predefined-macros.md)或定義為0時， **iscsym**和**iscsymf**才會定義為宏。否則它們會是未定義的。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**iscsym**、 **iscsymf**、 **__iscsym**、 **__iswcsym**、 **__iscsymf**、 **__iswcsymf**、 **_iscsym_l**、 **_iswcsym_l**、 **_iscsymf_l**、 **_iswcsymf_l**|C: \<ctype.h><br /><br /> C++: \<cctype> 或 \<ctype.h>|

**Iscsym**、 **iscsymf**、 **__iscsym**、 **__iswcsym**、 **__iscsymf**、 **__iswcsymf**、 **_iscsym_l**、 **_iswcsym_l**、 **_iscsymf_l**和 **_iswcsymf_l**常式都是 Microsoft 專有的。 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[字元分類](../../c-runtime-library/character-classification.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[is、isw 常式](../../c-runtime-library/is-isw-routines.md)<br/>

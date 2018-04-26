---
title: toascii、__toascii | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- __toascii
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- __toascii
- toascii
- ctype/toascii
- ctype/__toascii
dev_langs:
- C++
helpviewer_keywords:
- toascii function
- string conversion, to ASCII characters
- __toascii function
- ASCII characters, converting to
ms.assetid: a07c0608-b0e2-4da2-a20c-7b64d6a9b77c
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 62b94724e95738c424ee04b0fbccfad1fdf6951c
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="toascii-toascii"></a>toascii、__toascii

透過截斷將字元轉換成 7 位元 ASCII 字元。

## <a name="syntax"></a>語法

```C
int __toascii(
   int c
);
#define toascii __toascii
```

### <a name="parameters"></a>參數

*C*<br/>
要轉換的字元。

## <a name="return-value"></a>傳回值

**__toascii**的值，轉換*c*到 7 位元 ASCII 範圍，並傳回結果。 沒有表示錯誤的保留傳回值。

## <a name="remarks"></a>備註

**__Toascii**常式將指定的字元轉換為 ASCII 字元藉由截斷到低序位 7 位元。 不會套用任何其他轉換。

**__Toascii**常式已定義為巨集，除非已定義前置處理器巨集 _CTYPE_DISABLE_MACROS。 回溯相容性， **toascii**定義為巨集時，才[ &#95; &#95;STDC&#95; &#95; ](../../preprocessor/predefined-macros.md)未定義或定義為 0; 否則為未定義。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**toascii**， **__toascii**|C: \<ctype.h><br /><br /> C++: \<cctype> 或 \<ctype.h>|

**Toascii**巨集是 POSIX 擴充功能，和 **__toascii**是 POSIX 延伸模組的 Microsoft 特定實作。 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[is、isw 常式](../../c-runtime-library/is-isw-routines.md)<br/>
[to 函式](../../c-runtime-library/to-functions.md)<br/>

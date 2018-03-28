---
title: _ltoa、_ltow | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _ltoa
- _ltow
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
apitype: DLLExport
f1_keywords:
- ltow
- _ltot
- _ltoa
- _ltow
dev_langs:
- C++
helpviewer_keywords:
- converting integers
- _ltoa function
- _ltow function
- ltow function
- ltoa function
- long integer conversion to string
- converting numbers, to strings
ms.assetid: 14036104-2c25-4759-87c0-918ed8521e47
caps.latest.revision: ''
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 25dc7c06f2e5eadacb568a096fda30f81a16570b
ms.sourcegitcommit: 1d11412c8f5e6ddf4edded89e0ef5097cc89f812
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2018
---
# <a name="ltoa-ltow"></a>_ltoa、_ltow
將長整數轉換為字串。 這些函式已有更安全的版本可用，請參閱 [_ltoa_s、_ltow_s](../../c-runtime-library/reference/ltoa-s-ltow-s.md)。  
  
## <a name="syntax"></a>語法  
  
```  
char *_ltoa(  
   long value,  
   char *str,  
   int radix   
);  
wchar_t *_ltow(  
   long value,  
   wchar_t *str,  
   int radix   
);  
template <size_t size>  
char *_ltoa(  
   long value,  
   char (&str)[size],  
   int radix   
); // C++ only  
template <size_t size>  
wchar_t *_ltow(  
   long value,  
   wchar_t (&str)[size],  
   int radix   
); // C++ only  
```  
  
#### <a name="parameters"></a>參數  
 `value`  
 要轉換的數字。  
  
 `str`  
 字串結果。  
  
 `radix`  
 `value` 的底數。  
  
## <a name="return-value"></a>傳回值  
 所有這些函式都會傳回 `str` 的指標。 不會傳回錯誤。  
  
## <a name="remarks"></a>備註  
 `_ltoa` 函式會將 `value` 的數字轉換為以 Null 結束的字元字串，並將結果 (最多 33 個位元組) 儲存為 `str`。 `radix`引數指定的基底`value`，這必須在範圍 2-36。 如果`radix`等於 10 和`value`是負數，預存字串的第一個字元是減號 （-）。 `_ltow`是 `_ltoa` 的寬字元版本，第二個引數與 `_ltow` 的傳回值是寬字元字串。 所有這些函式都是 Microsoft 特定的函式。  
  
> [!IMPORTANT]
>  若要防止緩衝區溢位，請確定 `str` 緩衝區夠大，足以容納轉換的數字加上尾端的 Null 字元和符號字元。  
  
 在 C++ 中，這些函式具有範本多載。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_ltot`|`_ltoa`|`_ltoa`|`_ltow`|  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_ltoa`|\<stdlib.h>|  
|`_ltow`|\<stdlib.h>|  
  
 如需相容性詳細資訊，請參閱簡介中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>範例  
 請參閱 [_itoa](../../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md) 的範例。  
  
## <a name="see-also"></a>另請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [_itoa、_i64toa、_ui64toa、_itow、_i64tow、_ui64tow](../../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md)   
 [_ultoa、_ultow](../../c-runtime-library/reference/ultoa-ultow.md)
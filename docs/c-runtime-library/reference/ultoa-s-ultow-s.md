---
title: "_ultoa_s、_ultow_s | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ultow_s
- _ultoa_s
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
- _ultow_s
- ultoa_s
- ultow_s
- _ultoa_s
dev_langs: C++
helpviewer_keywords:
- _ultoa_s function
- converting integers
- integers, converting
- _ultow_s function
- ultoa_s function
- converting numbers, to strings
- ultow_s function
ms.assetid: 606ce905-6752-46ac-a15a-bdc22920e1d4
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7968e8f7eb3d69ec40d0fddab75ec2abee348823
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="ultoas-ultows"></a>_ultoa_s、_ultow_s
將不帶正負號的長整數轉換為字串。 這些是 [_ultoa、_ultow](../../c-runtime-library/reference/ultoa-ultow.md) 的版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。  
  
## <a name="syntax"></a>語法  
  
```  
errno_t _ultoa_s(  
    unsigned long value,  
    char *str,  
    size_t sizeOfstr,  
    int radix   
);  
errno_t _ultow_s(  
    unsigned long value,  
    wchar_t *str,  
    size_t sizeOfstr,  
    int radix   
);  
template <size_t size>  
errno_t _ultoa_s(  
    unsigned long value,  
    char (&str)[size],  
    int radix   
); // C++ only  
template <size_t size>  
errno_t _ultow_s(  
    unsigned long value,  
    wchar_t (&str)[size],  
    int radix   
); // C++ only  
```  
  
#### <a name="parameters"></a>參數  
 `value`  
 要轉換的數字。  
  
 `str`  
 字串結果。  
  
 `sizeOfstr`  
 `str` 的大小。若為 `_ultoa_s`，則以位元組為單位；若為 `_ultow_s`，則以字組為單位。  
  
 `radix`  
 `value` 的底數。  
  
## <a name="return-value"></a>傳回值  
 如果函式成功，則為零；否則為錯誤碼。  
  
## <a name="remarks"></a>備註  
 `_ultoa_s` 函式會將 `value` 的數字轉換為以 Null 結束的字元字串，並將結果 (最多 33 個位元組) 儲存為 `str`。 `radix`引數指定的基底`value`，這必須在範圍 2-36。 `_ultow_s` 是寬字元版本的 `_ultoa_s`；`_ultow_s` 的第二個引數是寬字元字串。  
  
 如果 `str` 為 `NULL` 指標，或如果 `sizeOfstr` 小於或等於零，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會傳回 -1，並將 `errno` 設定為 `EINVAL`；如果 `value` 或 `str` 超出長整數的範圍，這些函式會傳回 -1，並將 `errno` 設定為 `ERANGE`。  
  
 C++ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 (因而不須指定大小引數)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_ultot_s`|`_ultoa_s`|`_ultoa_s`|`_ultow_s`|  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_ultoa_s`|\<stdlib.h>|  
|`_ultow_s`|\<stdlib.h>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="see-also"></a>另請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [_ultoa、_ultow](../../c-runtime-library/reference/ultoa-ultow.md)   
 [_ltoa、_ltow](../../c-runtime-library/reference/ltoa-ltow.md)   
 [_ltoa_s、_ltow_s](../../c-runtime-library/reference/ltoa-s-ltow-s.md)   
 [_ltoa_s、_ltow_s](../../c-runtime-library/reference/ltoa-s-ltow-s.md)
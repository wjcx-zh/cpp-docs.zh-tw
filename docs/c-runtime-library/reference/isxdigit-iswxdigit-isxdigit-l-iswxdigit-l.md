---
title: "isxdigit、iswxdigit、_isxdigit_l、_iswxdigit_l | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _iswxdigit_l
- iswxdigit
- isxdigit
- _isxdigit_l
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
- iswxdigit
- isxdigit
- _istxdigit
dev_langs: C++
helpviewer_keywords:
- isxdigit function
- istxdigit function
- _iswxdigit_l function
- _istxdigit function
- _isxdigit_l function
- iswxdigit_l function
- isxdigit_l function
- hexadecimal characters
- iswxdigit function
ms.assetid: c8bc5146-0b58-4e3f-bee3-f2318dd0f829
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1ba714f78696cd806cbf1f200e72e09a03168d94
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="isxdigit-iswxdigit-isxdigitl-iswxdigitl"></a>isxdigit、iswxdigit、_isxdigit_l、_iswxdigit_l
判斷整數是否為代表十六進位數字的字元。  
  
## <a name="syntax"></a>語法  
  
```  
int isxdigit(  
   int c   
);  
int iswxdigit(  
   wint_t c   
);  
int _isxdigit_l(  
   int c,  
   _locale_t locale  
);  
int _iswxdigit_l(  
   wint_t c,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>參數  
 `c`  
 待測試整數。  
  
 `locale`  
 要使用的地區設定。  
  
## <a name="return-value"></a>傳回值  
 如果 `c` 表示特定的十六進位數字，這些常式都會傳回非零值。 `isxdigit`傳回非零值，如果`c`是十六進位數字 (A-F，a-f 或 0-9)。 如果 `c` 是與十六進位數字字元對應的寬字元，則 `iswxdigit` 會傳回非零值。 如果 `c` 不符合測試條件，這些常式都會傳回 0。  
  
 針對 "C"地區設定，`iswxdigit` 函式不支援 Unicode 全形十六進位字元。  
  
 這些具有 `_l` 尾碼的函式版本會使用傳入的地區設定參數來處理其地區設定相關行為，而不使用目前的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。  
  
 如果 `c` 不是 EOF 或介於 0 到 0xFF 的內含範圍中，則 `isxdigit` 和 `_isxdigit_l` 的行為是未定義的。 當使用 CRT 偵錯程式庫，而 `c` 不是其中一個值時，函式會引發判斷提示。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_istxdigit`|`isxdigit`|`isxdigit`|`iswxdigit`|  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`isxdigit`|\<ctype.h>|  
|`iswxdigit`|\<ctype.h> 或 \<wchar.h>|  
|`_isxdigit_l`|\<ctype.h>|  
|`_iswxdigit_l`|\<ctype.h> 或 \<wchar.h>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>請參閱  
 [字元分類](../../c-runtime-library/character-classification.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [is、isw 常式](../../c-runtime-library/is-isw-routines.md)
---
title: "ispunct、iswpunct、_ispunct_l、_iswpunct_l | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- ispunct
- _iswpunct_l
- iswpunct
- _ispunct_l
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
- iswpunct
- _istpunct
- ispunct
dev_langs: C++
helpviewer_keywords:
- _istpunct function
- _ispunct_l function
- iswpunct function
- ispunct function
- istpunct function
- ispunct_l function
- _iswpunct_l function
- iswpunct_l function
ms.assetid: 94403240-85c8-40a4-9c2b-e3e95c729c76
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9856ed0cb5f4ea9a346f07c4ad98a8cf7c534f61
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ispunct-iswpunct-ispunctl-iswpunctl"></a>ispunct、iswpunct、_ispunct_l、_iswpunct_l
判斷整數是否代表標點符號字元。  
  
## <a name="syntax"></a>語法  
  
```  
int ispunct(  
   int c   
);  
int iswpunct(  
   wint_t c   
);  
int _ispunct_l(  
   int c,  
   _locale_t locale  
);  
int _iswpunct_l(  
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
 如果 `c` 表示特定的標點符號字元，這些常式都會傳回非零值。 針對任何不是空白字元的可列印字元或 `isalnum` 為非零值的字元，`ispunct` 會傳回非零值。 針對任何既非空格寬字元，亦非 `iswalnum` 為非零值的寬字元的可列印字元，`iswpunct` 會傳回非零值。 如果 `c` 不符合測試條件，這些常式都會傳回 0。  
  
 `ispunct` 函式測試條件的結果取決於地區設定的 `LC_CTYPE` 類別設定；如需詳細資訊，請參閱 [setlocale、_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。 這些沒有 `_l` 尾碼的函式版本使用目前地區設定來處理任何地區設定相關行為；具有 `_l` 尾碼的版本則完全相同，但會改用傳入的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。  
  
 如果 `c` 不是 EOF 或介於 0 到 0xFF 的內含範圍中，則 `ispunct` 和 `_ispunct_l` 的行為是未定義的。 當使用 CRT 偵錯程式庫，而 `c` 不是其中一個值時，函式會引發判斷提示。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|**_** `istpunct`|`ispunct`|[_ismbcpunct](../../c-runtime-library/reference/ismbcgraph-functions.md)|`iswpunct`|  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`ispunct`|\<ctype.h>|  
|`iswpunct`|\<ctype.h> 或 \<wchar.h>|  
|`_ispunct_l`|\<ctype.h>|  
|`_iswpunct_l`|\<ctype.h> 或 \<wchar.h>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>請參閱  
 [字元分類](../../c-runtime-library/character-classification.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [is、isw 常式](../../c-runtime-library/is-isw-routines.md)
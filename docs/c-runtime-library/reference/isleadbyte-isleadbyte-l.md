---
title: "isleadbyte、_isleadbyte_l | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _isleadbyte_l
- isleadbyte
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
- _istleadbyte
- _isleadbyte_l
- isleadbyte
dev_langs:
- C++
helpviewer_keywords:
- lead bytes
- _isleadbyte_l function
- _istleadbyte function
- istleadbyte function
- isleadbyte function
ms.assetid: 3b2bcf09-d82b-4803-9e80-59d04942802a
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 73078df22931a5533ffe912174d11b384c8de417
ms.contentlocale: zh-tw
ms.lasthandoff: 04/01/2017

---
# <a name="isleadbyte-isleadbytel"></a>isleadbyte、_isleadbyte_l
判斷某個字元是否為多位元組字元的前導位元組。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱                  [/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>語法  
  
```  
int isleadbyte(  
   int c   
);  
int _isleadbyte_l(  
   int c   
);  
```  
  
#### <a name="parameters"></a>參數  
 `c`  
 待測試整數。  
  
## <a name="return-value"></a>傳回值  
 如果引數符合測試條件，`isleadbyte` 會傳回非零值，否則會傳回 0。 在 "C" 地區設定和單一位元組字元集 (SBCS) 地區設定中， `isleadbyte` 一律會傳回 0。  
  
## <a name="remarks"></a>備註  
 如果 `isleadbyte` 巨集的引數是多位元組字元的第一個位元組，則該巨集會傳回非零值。 `isleadbyte`會產生有意義的結果的任何整數引數，介於-1 (`EOF`) 至`UCHAR_MAX`(0xFF)，（含)。  
  
 `isleadbyte` 的預期引數類型為 `int`；如果傳遞了帶正負號的字元，編譯器可能會將其轉換成帶正負號的整數，而產生無法預期的結果。  
  
 尾碼為 `_l` 的這個函式版本是一樣的，只不過與地區設定相關的行為使用了傳入的地區設定，而不是目前的地區設定。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_istleadbyte`|一律傳回 false|**_** `isleadbyte`|一律傳回 false|  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`isleadbyte`|\<ctype.h>|  
|`_isleadbyte_l`|\<ctype.h>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另請參閱  
 [位元組分類](../../c-runtime-library/byte-classification.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [_ismbb 常式](../../c-runtime-library/ismbb-routines.md)

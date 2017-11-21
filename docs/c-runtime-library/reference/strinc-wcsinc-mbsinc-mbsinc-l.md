---
title: "_strinc、_wcsinc、_mbsinc、_mbsinc_l | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbsinc
- _wcsinc
- _mbsinc_l
- _strinc
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
- mbsinc_l
- _strinc
- strinc
- _mbsinc
- _wcsinc
- wcsinc
- mbsinc
- _mbsinc_l
dev_langs: C++
helpviewer_keywords:
- _mbsinc function
- wcsinc function
- mbsinc_l function
- _strinc function
- strinc function
- _mbsinc_l function
- mbsinc function
- _wcsinc function
- _tcsinc function
- tcsinc function
ms.assetid: 54685943-8e2c-45e9-a559-2d94930dc6b4
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 04fb17130f82c4b34b461f9d4fe0880b1363d3c0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="strinc-wcsinc-mbsinc-mbsincl"></a>_strinc、_wcsinc、_mbsinc、_mbsinc_l
使字串指標前進一個字元。  
  
> [!IMPORTANT]
>  在 Windows 執行階段中執行的應用程式中無法使用 `_mbsinc` 和 `_mbsinc_l`。 如需詳細資訊，請參閱 [/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>語法  
  
```  
char *_strinc(  
   const char *current,  
   _locale_t locale  
);  
wchar_t *_wcsinc(  
   const wchar_t *current,  
   _locale_t locale  
);  
unsigned char *_mbsinc(  
   const unsigned char *current   
);  
unsigned char *_mbsinc_l(  
   const unsigned char *current,  
   _locale_t locale  
);  
  
```  
  
#### <a name="parameters"></a>參數  
 `current`  
 字元指標。  
  
 `locale`  
 要使用的地區設定。  
  
## <a name="return-value"></a>傳回值  
 這些常式每個都會傳回緊接在 `current` 之後的字元的指標。  
  
## <a name="remarks"></a>備註  
 `_mbsinc` 會傳回緊接在 `current` 之後的多位元組字元中第一個位元組的指標。 `_mbsinc` 會根據目前使用的[多位元組字碼頁](../../c-runtime-library/code-pages.md)來辨識多位元組字元序列；`_mbsinc_l` 與其相同，只不過它會改用傳入的地區設定參數。 如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 若已定義 `_tcsinc`，定義於 Tchar.h 中的一般文字函式 `_mbsinc` 會對應至 `_MBCS`；若已定義 `_wcsinc`，則該函式會對應至 `_UNICODE`。 若兩者皆否，則 `_tcsinc` 會對應至 `_strinc`。 `_strinc` 和 `_wcsinc` 分別是單一位元組字元版本和寬字元版本的 `_mbsinc`。 只有針對此對應才提供 `_strinc` 和 `_wcsinc`，除此之外都不應使用。 如需詳細資訊，請參閱[使用泛型文字對應](../../c-runtime-library/using-generic-text-mappings.md)以及[泛型文字對應](../../c-runtime-library/generic-text-mappings.md)。  
  
 如果 `current` 為 `NULL`，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行，此函式會傳回 `EINVAL`，並將 `errno` 設為 `EINVAL`。  
  
> [!IMPORTANT]
>  這些函式可能容易受到緩衝區滿溢的威脅。 緩衝區滿溢可能被當成系統攻擊方式，因為它們可能導致非預期的提高權限。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_mbsinc`|\<mbstring.h>|  
|`_mbsinc_l`|\<mbstring.h>|  
|`_strinc`|\<tchar.h>|  
|`_wcsinc`|\<tchar.h>|  
  
 如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [_strdec、_wcsdec、_mbsdec、_mbsdec_l](../../c-runtime-library/reference/strdec-wcsdec-mbsdec-mbsdec-l.md)   
 [_strnextc、_wcsnextc、_mbsnextc、_mbsnextc_l](../../c-runtime-library/reference/strnextc-wcsnextc-mbsnextc-mbsnextc-l.md)   
 [_strninc、_wcsninc、_mbsninc、_mbsninc_l](../../c-runtime-library/reference/strninc-wcsninc-mbsninc-mbsninc-l.md)
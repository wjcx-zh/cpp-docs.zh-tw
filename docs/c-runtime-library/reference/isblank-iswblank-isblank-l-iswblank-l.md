---
title: "isblank、iswblank、_isblank_l、_iswblank_l | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- isblank
- _isblank_l
- iswblank
- _iswblank_l
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
- _iswblank_l
- isblank
- _istblank_l
- _istblank
- _isblank_l
- iswblank
dev_langs:
- C++
ms.assetid: 33ce96c0-f387-411a-8283-c3d2a69e56bd
caps.latest.revision: 4
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
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
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 6c5f3ebe9921a4b8cc4781cf81239fd63dfa7fd2
ms.contentlocale: zh-tw
ms.lasthandoff: 03/30/2017

---
# <a name="isblank-iswblank-isblankl-iswblankl"></a>isblank、iswblank、_isblank_l、_iswblank_l
判斷整數是否代表空白字元。  
  
## <a name="syntax"></a>語法  
  
```  
int isblank(  
   int c   
);  
int iswblank(  
   wint_t c   
);  
int _isblank_l(  
   int c,  
   _locale_t locale  
);  
int _iswblank_l(  
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
 如果 `c` 表示特定的空格或水平索引標籤字元，或是特定地區設定中用來分隔一行文字中單字的字元組之一，則這些常式都會傳回非零。 如果 `c` 為空白字元 (0x20) 或水平索引標籤字元 (0x09)，則 `isblank` 會傳回非零值。 `isblank`函式測試條件的結果取決於地區設定的 `LC_CTYPE` 類別設定；如需詳細資訊，請參閱 [setlocale、_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。 這些沒有 `_l` 尾碼的函式版本使用目前地區設定來處理任何地區設定相關行為；具有 `_l` 尾碼的版本則完全相同，但會改用傳入的地區設定。 如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 如果 `c` 是對應至標準空格或水平索引標籤字元的寬字元，則 `iswblank` 會傳回非零值。  
  
 如果 `c` 不是 EOF 或介於 0 到 0xFF 的內含範圍中，則 `isblank` 和 `_isblank_l` 的行為是未定義的。 當使用 CRT 偵錯程式庫，而 `c` 不是其中一個值時，函式會引發判斷提示。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_istblank`|`isblank`|[_ismbcblank](../../c-runtime-library/reference/ismbcgraph-functions.md)|`iswblank`|  
|`_istblank_l`|`_isblank_l`|[_ismbcblank_l](../../c-runtime-library/reference/ismbcgraph-functions.md)|`_iswblank_l`|  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`isblank`|\<ctype.h>|  
|`iswblank`|\<ctype.h> 或 \<wchar.h>|  
|`_isblank_l`|\<ctype.h>|  
|`_iswblank_l`|\<ctype.h> 或 \<wchar.h>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另請參閱  
 [字元分類](../../c-runtime-library/character-classification.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [is、isw 常式](../../c-runtime-library/is-isw-routines.md)

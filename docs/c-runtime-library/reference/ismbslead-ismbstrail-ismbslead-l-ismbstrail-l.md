---
title: "_ismbslead、_ismbstrail、_ismbslead_l、_ismbstrail_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_ismbstrail"
  - "_ismbslead_l"
  - "_ismbslead"
  - "_ismbstrail_l"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-multibyte-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_ismbslead"
  - "ismbs"
  - "ismbslead_l"
  - "_ismbs"
  - "ismbstrail_l"
  - "ismbslead"
  - "_ismbstrail"
  - "_ismbstrail_l"
  - "ismbstrail"
  - "_ismbslead_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ismbslead 函式"
  - "_ismbslead_l 函式"
  - "_ismbstrail 函式"
  - "_ismbstrail_l 函式"
  - "ismbslead 函式"
  - "ismbslead_l 函式"
  - "ismbstrail 函式"
  - "ismbstrail_l 函式"
ms.assetid: 86d2cd7a-3cff-443a-b713-14cc17a231e9
caps.latest.revision: 22
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ismbslead、_ismbstrail、_ismbslead_l、_ismbstrail_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

執行多位元組字元字串前導位元組和後隨位元組的即時線上測試，並判斷指定的子字串指標是否指向前導位元組或後隨位元組。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
int _ismbslead(  
   const unsigned char *str,  
   const unsigned char *current   
);  
int _ismbstrail(  
   const unsigned char *str,  
   const unsigned char *current   
);  
int _ismbslead_l(  
   const unsigned char *str,  
   const unsigned char *current,  
   _locale_t locale  
);  
int _ismbstrail_l(  
   const unsigned char *str,  
   const unsigned char *current,  
   _locale_t locale  
);  
```  
  
#### 參數  
 `str`  
 指向字串開頭或先前已知的前導位元組之指標。  
  
 `current`  
 在字串要進行測試的位置之指標。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 如果該字元是前導位元組，則 `_ismbslead` 會傳回 –1，而如果該字元是後隨位元組，則 `_ismbstrail` 會傳回 –1。  如果輸入字串有效，但不是前導位元組或後隨位元組，則這些函式會傳回零。  如果有任一個引數是 `NULL`，則會叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，這些函式會傳回 `NULL`，並將 `errno` 設為 `EINVAL`。  
  
## 備註  
 因為字串內容也列入考量，`_ismbslead` 和 `_ismbstrail` 比 `_ismbblead` 和 `_ismbbtrail` 版本慢。  
  
 這些有 `_l` 尾碼的函式版本都相同，不同之處在其與地區設定相關的行為，它們會使用傳入的地區設定參數，而不使用目前的地區設定。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
## 需求  
  
|常式|必要的標頭|選擇性標頭|  
|--------|-----------|-----------|  
|`_ismbslead`|\<mbctype.h\> 或 \<mbstring.h\>|\<ctype.h\>、\* \<limits.h\>、\<stdlib.h\>|  
|`_ismbstrail`|\<mbctype.h\> 或 \<mbstring.h\>|\<ctype.h\>、\* \<limits.h\>、\<stdlib.h\>|  
|`_ismbslead_l`|\<mbctype.h\> 或 \<mbstring.h\>|\<ctype.h\>、\* \<limits.h\>、\<stdlib.h\>|  
|`_ismbstrail_l`|\<mbctype.h\> 或 \<mbstring.h\>|\<ctype.h\>、\* \<limits.h\>、\<stdlib.h\>|  
  
 \* 針對此測試條件的資訊清單常數。  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [字元分類](../../c-runtime-library/character-classification.md)   
 [\_ismbc 常式](../../c-runtime-library/ismbc-routines.md)   
 [is、isw 常式](../../c-runtime-library/is-isw-routines.md)   
 [\_ismbb 常式](../../c-runtime-library/ismbb-routines.md)
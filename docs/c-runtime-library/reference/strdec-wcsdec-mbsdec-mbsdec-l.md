---
title: "_strdec、_wcsdec、_mbsdec、_mbsdec_l | Microsoft Docs"
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
  - "_wcsdec"
  - "_strdec"
  - "_mbsdec"
  - "_mbsdec_l"
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
  - "_strdec"
  - "mbsdec_l"
  - "strdec"
  - "_mbsdec"
  - "_mbsdec_l"
  - "mbsdec"
  - "wcsdec"
  - "_wcsdec"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mbsdec 函式"
  - "_mbsdec_l 函式"
  - "_strdec 函式"
  - "_tcsdec 函式"
  - "_wcsdec 函式"
  - "mbsdec 函式"
  - "mbsdec_l 函式"
  - "strdec 函式"
  - "tcsdec 函式"
  - "wcsdec 函式"
ms.assetid: ae37c223-800f-48a9-ae8e-38c8d20af2dd
caps.latest.revision: 24
caps.handback.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _strdec、_wcsdec、_mbsdec、_mbsdec_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將資料指標向後移動一個字元  
  
> [!IMPORTANT]
>  `mbsdec` 與`mbsdec_l`不能用於[!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
unsigned char *_strdec(  
   const unsigned char *start,  
   const unsigned char *current   
);  
unsigned wchar_t *_wcsdec(  
   const unsigned wchar_t *start,  
   const unsigned wchar_t *current   
);  
unsigned char *_mbsdec(  
   const unsigned char *start,  
   const unsigned char *current   
);  
unsigned char *_mbsdec_l(  
   const unsigned char *start,  
   const unsigned char *current,  
   _locale_t locale  
);  
```  
  
#### 參數  
 `start`  
 對任何字元的指標 \( `_mbsdec` \) 和`mbsdec_l`，第一個位元組的任何多位元組字元\) 在來源字串; `start` 必須在來源字串的 `current` 之前。  
  
 `current`  
 對在來源字串任何字元的指標 \( 或是對於`_mbsdec` \) 和`mbsdec_l`，第一個位元組的任何多位元組字元\) ; `current` 必須在來源字串的 `start` 之後。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 `_mbsdec`, \_`mbsdec_l`, `_strdec` 和 `_wcsdec` 每個回傳緊接在字元後的指標 `current`; `_mbsdec` 如果`start`值大於或等於 `current`的值，回傳 `NULL` 。  `_tcsdec` 對應到這些函式之一，而它的傳回值取決於對應的函式。  
  
## 備註  
 `_mbsdec` 和 `_mbsdec_l` 函式會傳回指標緊接在該字串的 `current` 之前包含 `start`多位元組字元的第一個位元組。  
  
 輸出值受地區設定的 `LC_CTYPE` 類別設定的設定所影響; 請參閱 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) 以取得詳細資訊。 `_mbsdec` 表示根據目前使用的地區設定識別多位元組字元序列，而 `_mbsdec_l` 除了使用傳遞的地區設定參數之外都相同。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 如果 `start` 或 `current` 是 `NULL`，會觸發無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，這個函式會傳回 `EINVAL`，並將 `errno` 設為 `EINVAL`。  
  
> [!IMPORTANT]
>  這些函式可能容易受到緩衝區滿溢的威脅。  緩衝區滿溢可能被當成系統攻擊方式，因為它們可能導致非預期的提高權限。  如需詳細資訊，請參閱 [Avoiding Buffer Overruns](http://msdn.microsoft.com/library/windows/desktop/ms717795) 。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|------------------------------|----------------|-------------------|  
|`_tcsdec`|`_strdec`|`_mbsdec`|`_wcsdec`|  
  
 `_strdec` 和 `_wcsdec` 是 `_mbsdec` 和 `_mbsdec_l`的單位元組字元和寬字元版本。  `_strdec` 和 `_wcsdec` 只提供這種對應使用，並且不應該為其他用途所使用。  
  
 如需詳細資訊，請參閱[使用泛型文字對應](../../c-runtime-library/using-generic-text-mappings.md)與[泛型文字對應](../../c-runtime-library/generic-text-mappings.md)。  
  
## 需求  
  
|常式|必要的標頭|選擇性標頭|  
|--------|-----------|-----------|  
|`_mbsdec`|\<mbstring.h\>|\<mbctype.h\>|  
|`_mbsdec_l`|\<mbstring.h\>|\<mbctype.h\>|  
|`_strdec`|\<tchar.h\>||  
|`_wcsdec`|\<tchar.h\>||  
  
 如需詳細的相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 下列範例顯示如何使用 `_tcsdec`。  
  
```  
#include <iostream>  
#include <tchar.h>  
using namespace std;  
  
int main()  
{  
   const TCHAR *str = _T("12345");  
   cout << "str: " << str << endl;  
  
   const TCHAR *str2;  
   str2 = str + 2;  
   cout << "str2: " << str2 << endl;  
  
   TCHAR *answer;  
   answer = _tcsdec( str, str2 );  
   cout << "answer: " << answer << endl;  
  
   return (0);   
}  
  
```  
  
 下列範例顯示如何使用 `_mbsdec`。  
  
```  
#include <iostream>  
#include <mbstring.h>  
using namespace std;  
  
int main()   
{   
   char *str = "12345";  
   cout << "str: " << str << endl;  
  
   char *str2;  
   str2 = str + 2;   
   cout << "str2: " << str2 << endl;  
  
   unsigned char *answer;  
   answer = _mbsdec( reinterpret_cast<unsigned char *>( str ), reinterpret_cast<unsigned char *>( str2 ));  
  
   cout << "answer: " << answer << endl;  
  
   return (0);   
}  
  
```  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [\_strinc、\_wcsinc、\_mbsinc、\_mbsinc\_l](../../c-runtime-library/reference/strinc-wcsinc-mbsinc-mbsinc-l.md)   
 [\_strnextc、\_wcsnextc、\_mbsnextc、\_mbsnextc\_l](../../c-runtime-library/reference/strnextc-wcsnextc-mbsnextc-mbsnextc-l.md)   
 [\_strninc、\_wcsninc、\_mbsninc、\_mbsninc\_l](../../c-runtime-library/reference/strninc-wcsninc-mbsninc-mbsninc-l.md)
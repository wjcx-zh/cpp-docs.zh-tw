---
title: "_getch、_getwch | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _getch
- _getwch
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
- api-ms-win-crt-conio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- getwch
- _getch
- _getwch
dev_langs:
- C++
helpviewer_keywords:
- characters, getting from console
- getch function
- _getwch function
- console, reading from
- _getch function
- getwch function
ms.assetid: cc116be7-cff2-4274-970f-5e7b18ccc05c
caps.latest.revision: 26
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
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: d5f2d015ecc2f027712bc81f1ea538f88e130662
ms.lasthandoff: 02/24/2017

---
# <a name="getch-getwch"></a>_getch、_getwch
在不回應的情形下，從主控台取得字元。  
  
> [!IMPORTANT]
>  這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>語法  
  
```  
int _getch( void );  
wint_t _getwch( void );  
```  
  
## <a name="return-value"></a>傳回值  
 傳回讀取的字元。 不會傳回錯誤。  
  
## <a name="remarks"></a>備註  
 `_getch` 和 `_getwch` 函式從主控台讀取單一字元，且不回應該字元。 這些函式都不可以用來讀取 CTRL+C。 在讀取功能鍵或方向鍵時，每個函式必須呼叫兩次；第一次呼叫會傳回 0 或 0xE0，而第二次呼叫會傳回實際的按鍵碼。  
  
 這些函式鎖定呼叫執行緒，因此為安全執行緒。 如需非鎖定版本，請參閱 [_getch_nolock、_getwch_nolock](../../c-runtime-library/reference/getch-nolock-getwch-nolock.md)。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_gettch`|`_getch`|`_getch`|`_getwch`|  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_getch`|\<conio.h>|  
|`_getwch`|\<conio.h> 或 \<wchar.h>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_getch.c  
// compile with: /c  
// This program reads characters from  
// the keyboard until it receives a 'Y' or 'y'.  
  
#include <conio.h>  
#include <ctype.h>  
  
int main( void )  
{  
   int ch;  
  
   _cputs( "Type 'Y' when finished typing keys: " );  
   do  
   {  
      ch = _getch();  
      ch = toupper( ch );  
   } while( ch != 'Y' );  
  
   _putch( ch );  
   _putch( '\r' );    // Carriage return  
   _putch( '\n' );    // Line feed    
}  
```  
  
```Output  
  
abcdeyType 'Y' when finished typing keys: Y  
```  
  
## <a name="net-framework-equivalent"></a>NET Framework 對等  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另請參閱  
 [主控台和連接埠 I/O](../../c-runtime-library/console-and-port-i-o.md)   
 [_getche、_getwche](../../c-runtime-library/reference/getche-getwche.md)   
 [_cgets、_cgetws](../../c-runtime-library/cgets-cgetws.md)   
 [getc、getwc](../../c-runtime-library/reference/getc-getwc.md)   
 [_ungetch、_ungetwch、_ungetch_nolock、_ungetwch_nolock](../../c-runtime-library/reference/ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)

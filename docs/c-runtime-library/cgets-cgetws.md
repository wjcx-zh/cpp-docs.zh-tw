---
title: "_cgets、_cgetws | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _cgetws
- _cgets
apilocation:
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr110_clr0400.dll
apitype: DLLExport
f1_keywords:
- cgetws
- _cgetws
- _cgets
dev_langs:
- C++
helpviewer_keywords:
- _cgetws function
- strings [C++], getting from console
- console, getting strings from
- _cgets function
- cgetws function
- cgets function
ms.assetid: 4d5e134a-58c3-4f62-befd-5d235b0212f4
caps.latest.revision: 32
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 57e2d4bf3c84c44917ccfea8ca6584f1c94f5200
ms.contentlocale: zh-tw
ms.lasthandoff: 04/04/2017

---
# <a name="cgets-cgetws"></a>_cgets、_cgetws
從主控台取得字元字串。 這些函式已有更安全的版本，請參閱 [_cgets_s、_cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md)。  
  
> [!IMPORTANT]
>  這些函式已被取代。 自 Visual Studio 2015 起，這些函式即無法在 CRT 中使用。 這些函式 (_cgets_s 及 _cgetws_s) 的安全版本仍可使用。 如需這些替代函式的相關資訊，請參閱 [_cgets_s、_cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md)。  
  
> [!IMPORTANT]
>  這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>語法  
  
```  
char *_cgets(   
   char *buffer   
);  
wchar_t *_cgetws(  
   wchar_t *buffer  
);  
template <size_t size>  
char *_cgets(   
   char (&buffer)[size]  
); // C++ only  
template <size_t size>  
wchar_t *_cgetws(  
   wchar_t (&buffer)[size]  
); // C++ only  
```  
  
#### <a name="parameters"></a>參數  
 `buffer`  
 資料的儲存位置。  
  
## <a name="return-value"></a>傳回值  
 `_cgets` 和 `_cgetws` 會傳回位在 `buffer[2]` 的字串開頭指標。 如果 `buffer` 為 `NULL`，則這些函式會叫用無效的參數處理常式，如[參數驗證](../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行，這些函式將會傳回 `NULL` ，並將 `errno` 設為 `EINVAL`。  
  
## <a name="remarks"></a>備註  
 這些函式會從主控台讀取字元字串，並將字串及其長度儲存在 `buffer`指向的位置。 `buffer` 參數必須是指向字元陣列的指標。 陣列的第一個項目 `buffer[0]`必須包含要讀取之字串的長度上限 (字元)。 陣列必須包含足夠的項目，以容納字串、終止的 null 字元 ('\0') 及 2 個額外的位元組。 此函式會讀取歸位/換行字元 (CR-LF) 組合之前的所有字元，或讀取指定數量的字元。 字串會從 `buffer[2]`開始儲存。 若函式讀取了 CR LF，將會儲存 null 字元 ('\0')。 此函式會將該字串的實際長度儲存在第二個陣列項目 `buffer[1]`中。  
  
 因為在主控台視窗中呼叫 `_cgets` 或 `_cgetws` 時，所有編輯索引鍵都會在使用中，所以按 F3 鍵會重複上一個輸入的項目。  
  
 在 C++ 中，這些函式具有樣板多載，可以叫用這些函式的更新且安全的對應版本。 如需詳細資訊，請參閱[安全範本多載](../c-runtime-library/secure-template-overloads.md)。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_cgetts`|`_cgets`|`_cgets`|`_cgetws`|  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_cgets`|\<conio.h>|  
|`_cgetws`|\<conio.h> 或 \<wchar.h>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_cgets.c  
// compile with: /c /W3  
// This program creates a buffer and initializes  
// the first byte to the size of the buffer. Next, the  
// program accepts an input string using _cgets and displays  
// the size and text of that string.  
  
#include <conio.h>  
#include <stdio.h>  
#include <errno.h>  
  
int main( void )  
{  
   char buffer[83] = { 80 };  // Maximum characters in 1st byte  
   char *result;  
  
   printf( "Input line of text, followed by carriage return:\n");  
  
   // Input a line of text:  
   result = _cgets( buffer ); // C4996  
   // Note: _cgets is deprecated; consider using _cgets_s  
   if (!result)  
   {  
      printf( "An error occurred reading from the console:"  
              " error code %d\n", errno);  
   }  
   else  
   {     
      printf( "\nLine length = %d\nText = %s\n",  
              buffer[1], result );  
   }  
}  
```  
  
```Output  
  
      A line of input.Input line of text, followed by carriage return:  
Line Length = 16  
Text = A line of input.  
```  
  
## <a name="see-also"></a>另請參閱  
 [主控台和連接埠 I/O](../c-runtime-library/console-and-port-i-o.md)   
 [_getch、_getwch](../c-runtime-library/reference/getch-getwch.md)

---
title: "gets、_getws | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _getws
- gets
apilocation:
- msvcr80.dll
- msvcr90.dll
- msvcr120.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- _getts
- gets
- _getws
dev_langs: C++
helpviewer_keywords:
- getws function
- getts function
- _getws function
- lines, getting
- streams, getting lines
- _getts function
- gets function
- standard input, reading from
ms.assetid: 1ec2dd4b-f801-48ea-97c2-892590f16024
caps.latest.revision: "32"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6193445dace47b62cf8793d69ad45e0f73a2f10d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="gets-getws"></a>gets、_getws
從 `stdin` 資料流取得行。 這些函式已有更安全的版本，請參閱 [gets_s, _getws_s](../c-runtime-library/reference/gets-s-getws-s.md)。  
  
> [!IMPORTANT]
>  這些函式已被取代。 自 Visual Studio 2015 起，這些函式即無法在 CRT 中使用。 這些函式的安全版本，但 gets_s 及 _getws_s 仍可繼續使用。 如需這些替代函式的資訊，請參閱 [gets_s, _getws_s](../c-runtime-library/reference/gets-s-getws-s.md)。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>語法  
  
```  
char *gets(   
   char *buffer   
);  
wchar_t *_getws(   
   wchar_t *buffer   
);  
template <size_t size>  
char *gets(   
   char (&buffer)[size]  
); // C++ only  
template <size_t size>  
wchar_t *_getws(   
   wchar_t (&buffer)[size]  
); // C++ only  
```  
  
#### <a name="parameters"></a>參數  
 `buffer`  
 輸入字串的儲存體位置。  
  
## <a name="return-value"></a>傳回值  
 若成功，即傳回其引數。 `NULL` 指標表示錯誤或檔案結尾條件。 使用 [ferror](../c-runtime-library/reference/ferror.md) 或 [feof](../c-runtime-library/reference/feof.md) 判斷發生的是哪一個事件。 若 `buffer` 為 `NULL`，則這些函式將會叫用無效的參數處理常式，如 [Parameter Validation](../c-runtime-library/parameter-validation.md)。 若允許繼續執行，這些函式會傳回 `NULL` ，並將 errno 設為 `EINVAL`。  
  
## <a name="remarks"></a>備註  
 `gets` 函式會從標準輸入資料流 `stdin` 讀取一行，並將其儲存在 `buffer`中。 此行包括到第一個新行字元 ('\n') (含) 的所有字元。 `gets` 接著會取代以 null 字元 ('\0') 取代新行字元，然後再傳回該行。 相反地， `fgets` 函式則會保留新行字元。 `_getws` 是寬字元版的 `gets`，其引數與傳回值均為寬字元字串。  
  
> [!IMPORTANT]
>  因為無法限制 get 所能讀取的字元數，所以未經信任的輸入可能很容易就會造成緩衝區溢位。 請改用 `fgets` 。  
  
 在 C++ 中，這些函式具有樣板多載，可以叫用這些函式的更新且安全的對應版本。 如需詳細資訊，請參閱 [Secure Template Overloads](../c-runtime-library/secure-template-overloads.md)。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_getts`|`gets`|`gets`|`_getws`|  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`gets`|\<stdio.h>|  
|`_getws`|\<stdio.h> 或 \<wchar.h>|  
  
 如需其他相容性資訊，請參閱 [相容性](../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_gets.c  
// compile with: /WX /W3  
  
#include <stdio.h>  
  
int main( void )  
{  
   char line[21]; // room for 20 chars + '\0'  
   gets( line );  // C4996  
   // Danger: No way to limit input to 20 chars.  
   // Consider using gets_s instead.  
   printf( "The line entered was: %s\n", line );  
}  
```  
  
 請注意，輸入若是超過 20 個字元，將會導致行緩衝區溢位，而且幾近 100% 的機率會造成程式停止運作。  
  
```Output  
  
Hello there!The line entered was: Hello there!  
```  
  
## <a name="see-also"></a>請參閱  
 [資料流 I/O](../c-runtime-library/stream-i-o.md)   
 [fgets、fgetws](../c-runtime-library/reference/fgets-fgetws.md)   
 [fputs、fputws](../c-runtime-library/reference/fputs-fputws.md)   
 [puts、_putws](../c-runtime-library/reference/puts-putws.md)
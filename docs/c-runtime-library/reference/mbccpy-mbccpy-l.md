---
title: "_mbccpy、_mbccpy_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbccpy"
  - "_mbccpy_l"
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
  - "_mbccpy"
  - "tccpy"
  - "ftccpy"
  - "mbccpy"
  - "_tccpy"
  - "_ftccpy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mbccpy 函式"
  - "_mbccpy_l 函式"
  - "_tccpy 函式"
  - "_tccpy_l 函式"
  - "mbccpy 函式"
  - "mbccpy_l 函式"
  - "tccpy 函式"
  - "tccpy_l 函式"
ms.assetid: 13f4de6e-7792-41ac-b319-dd9b135433aa
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# _mbccpy、_mbccpy_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

複製某個字串的多位元組字元到另一個字串。  更多這些函式的可用安全版本，請參閱 [\_mbccpy\_s、\_mbccpy\_s\_l](../../c-runtime-library/reference/mbccpy-s-mbccpy-s-l.md)。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
void _mbccpy(  
   unsigned char *dest,  
   const unsigned char *src   
);  
void _mbccpy_l(  
   unsigned char *dest,  
   const unsigned char *src,  
   _locale_t locale  
);  
```  
  
#### 參數  
 `dest`  
 複製目的地。  
  
 `src`  
 要複製的多位元組字元。  
  
 `locale`  
 要使用的地區設定。  
  
## 備註  
 `_mbccpy` 函式將 `src` 的多位元組字元複製到 `dest`。  
  
 這個函式會驗證它的參數。  如果 `_mbccpy`傳遞 null 指標給`dest`或`src` ，則將會叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行， `errno` 將設定為 `EINVAL`。  
  
 `_mbccpy` 會在所有地區設定相依表現方式中使用目前的地區設定。  `_mbccpy_l` 與 `_mbccpy` 相似，除了`_mbccpy_l` 使用傳遞的地區設定為所有地區設定相關行為。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 **Security Note** 使用 null 結尾的字串。  null 結尾字串不能超過目的緩衝區的大小。  如需詳細資訊，請參閱 [Avoiding Buffer Overruns](http://msdn.microsoft.com/library/windows/desktop/ms717795) 。  緩衝區溢位問題是系統攻擊的常見方法，它會導致權限不確定性的增加。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|------------------------------|----------------|-------------------|  
|`_tccpy`|巨集或內嵌函式的對應|`_mbccpy`|巨集或內嵌函式的對應|  
|`_tccpy_l`|N\/A|`_mbccpy_l`|N\/A|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_mbccpy`|\<mbctype.h\>|  
|`_mbccpy_l`|\<mbctype.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## NET Framework 對等  
 不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_mbclen、mblen、\_mblen\_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)
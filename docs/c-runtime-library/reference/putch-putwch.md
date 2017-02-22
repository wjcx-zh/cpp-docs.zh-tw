---
title: "_putch、_putwch | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_putwch"
  - "_putch"
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
  - "api-ms-win-crt-conio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_putch"
  - "putwch"
  - "_putwch"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_putch 函式"
  - "_putwch 函式"
  - "字元, 撰寫"
  - "主控台, 將字元寫入"
  - "putch 函式"
  - "putwch 函式"
ms.assetid: 3babc7cf-e333-405d-8449-c788d61d51aa
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# _putch、_putwch
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將一個字元寫入控制項。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
  
      int _putch(  
int c   
);  
wint_t _putwch(  
   wchar_t c  
);  
```  
  
#### 參數  
 `c`  
 待輸出字元。  
  
## 傳回值  
 如果成功，會傳回 `c`。  如果 `_putch` 失敗，則會傳回 `EOF`;如果 **\_putwch** 失敗，則會傳回 **WEOF**。  
  
## 備註  
 這些函式會直接寫入`c` 字元到主控台，而不需要緩衝區。  在 Windows NT， **\_putwch** 使用目前主控台地區設定撰寫Unicode 字元。  
  
 與 **\_nolock** 結尾的版本相同，但不會防止被其他執行緒干擾。  如需詳細資訊，請參閱 `_putch_nolock`、`_putwch_nolock`。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|------------------------------|----------------|-------------------|  
|**\_puttch**|`_putch`|`_putch`|**\_putwch**|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_putch`|\<conio.h\>|  
|**\_putwch**|\<conio.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 範例  
 請參閱 [\_getch](../../c-runtime-library/reference/getch-getwch.md) 的範例。  
  
## 請參閱  
 [主控台和連接埠 I\/O](../../c-runtime-library/console-and-port-i-o.md)   
 [\_cprintf、\_cprintf\_l、\_cwprintf、\_cwprintf\_l](../../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)   
 [\_getch、\_getwch](../../c-runtime-library/reference/getch-getwch.md)
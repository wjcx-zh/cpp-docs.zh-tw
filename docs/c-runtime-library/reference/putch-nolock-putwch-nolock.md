---
title: "_putch_nolock、_putwch_nolock | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_putwch_nolock"
  - "_putch_nolock"
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
  - "_putch_nolock"
  - "_puttch_nolock"
  - "putch_nolock"
  - "putwch_nolock"
  - "_putwch_nolock"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_putch_nolock 函式"
  - "_puttch_nolock 函式"
  - "_putwch_nolock 函式"
  - "字元, 撰寫"
  - "主控台, 將字元寫入"
  - "putch_nolock 函式"
  - "puttch_nolock 函式"
  - "putwch_nolock 函式"
ms.assetid: edbc811d-bac6-47fa-a872-fe4f3a1590b0
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _putch_nolock、_putwch_nolock
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

寫入一個字元到主控台，而不用鎖定執行緒。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
  
      int _putch_nolock(  
int c   
);  
wint_t _putwch_nolock(  
wchar_t c  
);  
```  
  
#### 參數  
 *c*  
 待輸出字元。  
  
## 傳回值  
 如果成功，則傳回 *c*。  如果 **\_putch\_nolock** 失敗，則會傳回 **EOF**;如果 **\_putwch\_nolock** 失敗，則會傳回 **WEOF**。  
  
## 備註  
 **\_putch\_nolock** 和 **\_putwch\_nolock**  與 **\_putch** 和 **\_putwch**分別是相同的，除了它們不會受被其他執行緒干擾的保護。  因為它們不會造成鎖定其他執行緒的額外負荷，所以可能會比較快。  這些函式只能用在安全執行緒內容 \(例如單一執行緒應用程式\) 或呼叫範圍已經處理執行緒隔離的地方。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|------------------------------|----------------|-------------------|  
|**\_puttch\_nolock**|**\_putch\_nolock**|**\_putch\_nolock**|**\_putwch\_nolock**|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|**\_putch\_nolock**|\<conio.h\>|  
|**\_putwch\_nolock**|\<conio.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 請參閱  
 [主控台和連接埠 I\/O](../../c-runtime-library/console-and-port-i-o.md)   
 [\_cprintf、\_cprintf\_l、\_cwprintf、\_cwprintf\_l](../../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)   
 [\_getch、\_getwch](../../c-runtime-library/reference/getch-getwch.md)
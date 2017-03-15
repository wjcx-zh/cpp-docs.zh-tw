---
title: "_outp、_outpw、_outpd | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_outpd"
  - "_outp"
  - "_outpw"
apilocation: 
  - "msvcrt.dll"
  - "msvcr100.dll"
  - "msvcr120.dll"
  - "msvcr90.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr80.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_outpw"
  - "_outpd"
  - "_outp"
  - "outpd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_outp 函式"
  - "_outpd 函式"
  - "_outpw 函式"
  - "位元組, 寫入連接埠"
  - "Double Word"
  - "Double Word, 寫入連接埠"
  - "outp 函式"
  - "outpd 函式"
  - "outpw 函式"
  - "通訊埠, 寫入位元組位置"
  - "文字"
  - "文字, 寫入連接埠"
ms.assetid: c200fe22-41f6-46fd-b0be-ebb805b35181
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# _outp、_outpw、_outpd
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從連接埠輸出一個位元組 \(`_outp`\)、一個字組 \(`_outpw`\) 或雙字組 \(`_outpd`\)。  
  
> [!IMPORTANT]
>  這些函式已被取代。 自 Visual Studio 2015 起，這些函式即無法在 CRT 中使用。  
  
> [!IMPORTANT]
>  這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
  
int _outp(unsigned short port,int databyte);unsigned short _outpw(unsigned short port,unsigned short dataword);unsigned long _outpd(unsigned short port,unsigned long dataword);  
```  
  
#### 參數  
 *連接埠*  
 連接埠號碼。  
  
 *databyte, dataword*  
 輸出值。  
  
## 傳回值  
 這些函式會傳回資料輸出。 不會傳回錯誤。  
  
## 備註  
 `_outp`、`_outpw` 及 `_outpd` 函式會個別寫入一個位元組、一個字組及雙字組到指定的輸出連接埠。*port* 引數可以是介於 0\-65535 之間任何不帶正負號的整數。*databyte* 可以是介於 0\-255 之間的任何整數；*dataword* 可以位於整數、不帶正負號之短整數，或不帶正負號之長整數範圍內的任何值。  
  
 因為這些函式會直接寫入 I\/O 連接埠，所以無法在 Windows NT、Windows 2000、Windows XP 及 Windows Server 2003 的使用者程式碼中使用。 如需如何使用這些作業系統中之 I\/O 連接埠的資訊，請前往 MSDN 搜尋 "Serial Communications in Win32"。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_outp`|\<conio.h\>|  
|`_outpw`|\<conio.h\>|  
|`_outpd`|\<conio.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 所有版本的 [C 執行階段程式庫](../c-runtime-library/crt-library-features.md)。  
  
## 請參閱  
 [主控台和連接埠 I\/O](../c-runtime-library/console-and-port-i-o.md)   
 [\_inp、\_inpw、\_inpd](../c-runtime-library/inp-inpw-inpd.md)
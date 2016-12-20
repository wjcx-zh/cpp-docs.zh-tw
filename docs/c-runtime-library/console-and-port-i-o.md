---
title: "主控台和連接埠 I/O | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.io"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "I/O [CRT], 主控台"
  - "I/O [CRT], 連接埠"
  - "I/O 常式, 主控台和連接埠 I/O"
  - "通訊埠, I/O 常式"
  - "常式"
  - "常式, 主控台和連接埠 I/O"
ms.assetid: 0eee1c92-9b3d-41e0-a43a-257e546eeec8
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 主控台和連接埠 I/O
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這些常式讀取和寫入至主控台或在指定的連接埠。  主控台 I\/O 常式與資料流 I\/O 或低階 I\/O 程式庫常式相容。  I\/O 執行前，不需要開啟控制台或連接埠或關閉，因此未在此分類中的開啟或關閉的常式。  在 Windows 作業系統，從這些函式的輸出會導向至主控台，並無法重新導向。  
  
### 主控台和連接埠 I\/O 常式  
  
|常式|用法|  
|--------|--------|  
|[\_cgets, \_cgetws](../c-runtime-library/cgets-cgetws.md), [\_cgets\_s、\_cgetws\_s](../c-runtime-library/reference/cgets-s-cgetws-s.md)|從主控台讀取字串|  
|[\_cprintf， \_cwprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)， [\_cprintf\_s、\_cprintf\_s\_l、\_cwprintf\_s、\_cwprintf\_s\_l](../c-runtime-library/reference/cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)|將格式化資料寫入控制台。|  
|[\_cputs](../c-runtime-library/reference/cputs-cputws.md)|寫入資料至主控台|  
|[\_cscanf， \_cwscanf](../c-runtime-library/reference/cscanf-cscanf-l-cwscanf-cwscanf-l.md)， [\_cscanf\_s、\_cscanf\_s\_l、\_cwscanf\_s、\_cwscanf\_s\_l](../c-runtime-library/reference/cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)|從主控台讀取格式化資料|  
|[\_getch, \_getwch](../c-runtime-library/reference/getch-getwch.md)|從主控台讀取字元|  
|[\_getche, \_getwche](../c-runtime-library/reference/getch-getwch.md)|從主控台讀取字元並回應它|  
|[\_inp](../c-runtime-library/inp-inpw-inpd.md)|讀取指定的 I\/O 通訊的位元組。|  
|[\_inpd](../c-runtime-library/inp-inpw-inpd.md)|讀取指定的 I\/O 通訊之 Double 字組|  
|[\_inpw](../c-runtime-library/inp-inpw-inpd.md)|讀取指定的 I\/O 通訊的 2 位元組文字|  
|[\_kbhit](../c-runtime-library/reference/kbhit.md)|檢查在主控台的按鍵；在嘗試從主控台讀取前使用|  
|[\_outp](../c-runtime-library/outp-outpw-outpd.md)|將指定的輸入和輸出寫入一位元組|  
|[\_outpd](../c-runtime-library/outp-outpw-outpd.md)|對指定的 I\/O 通訊埠寫入 Double 字組|  
|[\_outpw](../c-runtime-library/outp-outpw-outpd.md)|對指定的 I\/O 通訊埠寫入 Double 字組|  
|[\_putch, \_putwch](../c-runtime-library/reference/putch-putwch.md)|寫入主控台字元|  
|[\_ungetch, \_ungetwch](../c-runtime-library/reference/ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)|「Unget」的最後一個字元從主控台讀取，因此變成讀取的下一個字元|  
  
## 請參閱  
 [輸入和輸出](../c-runtime-library/input-and-output.md)   
 [依分類區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)
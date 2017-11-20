---
title: "資料流狀態 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: streams, states
ms.assetid: 5f28c968-f132-403f-968c-8417ff315e52
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2e97f9a7f6d8953107e08b92189115213303e8ac
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="stream-states"></a>資料流狀態
資料流的有效狀態和狀態轉換如下圖所示。  
  
 ![資料流](../c-runtime-library/media/stream.gif "資料流")  
  
 每個圓圈都表示穩定的狀態。 每條線則表示對資料流進行函式呼叫後可能發生的轉換。 有五組函式會造成狀態轉換。  
  
 前三個群組中的函式在 \<stdio.h> 中宣告：  
  
-   位元組讀取函式 — [fgetc](../c-runtime-library/reference/fgetc-fgetwc.md)、[fgets](../c-runtime-library/reference/fgets-fgetws.md)、[fread](../c-runtime-library/reference/fread.md)、[fscanf](../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)、[getc](../c-runtime-library/reference/getc-getwc.md)、[getchar](../c-runtime-library/reference/getc-getwc.md)、[gets](../c-runtime-library/gets-getws.md)、[scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) 及 [ungetc](../c-runtime-library/reference/ungetc-ungetwc.md)  
  
-   位元組寫入函式 — [fprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)、[fputc](../c-runtime-library/reference/fputc-fputwc.md)、[fputs](../c-runtime-library/reference/fputs-fputws.md)、[fwrite](../c-runtime-library/reference/fwrite.md)、[printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)、[putc](../c-runtime-library/reference/putc-putwc.md)、[putchar](../c-runtime-library/reference/putc-putwc.md)、[puts](../c-runtime-library/reference/puts-putws.md)、[vfprintf](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md) 及 [vprintf](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)  
  
-   位置函式 — [fflush](../c-runtime-library/reference/fflush.md)、[fseek](../c-runtime-library/reference/fseek-fseeki64.md)、[fsetpos](../c-runtime-library/reference/fsetpos.md) 及 [rewind](../c-runtime-library/reference/rewind.md)  
  
 其餘兩個群組中的函式在 \<wchar.h> 中宣告：  
  
-   寬讀取函式 — [fgetwc](../c-runtime-library/reference/fgetc-fgetwc.md)、[fgetws](../c-runtime-library/reference/fgets-fgetws.md)、[fwscanf](../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)、[getwc](../c-runtime-library/reference/getc-getwc.md)、[getwchar](../c-runtime-library/reference/getc-getwc.md)、[ungetwc](../c-runtime-library/reference/ungetc-ungetwc.md) 及 [wscanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)，  
  
-   寬寫入函式 — [fwprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)、[fputwc](../c-runtime-library/reference/fputc-fputwc.md)、[fputws](../c-runtime-library/reference/fputs-fputws.md)、[putwc](../c-runtime-library/reference/putc-putwc.md)、[putwchar](../c-runtime-library/reference/fputc-fputwc.md)、[vfwprintf](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)、[vwprintf](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md) 及 [wprintf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)，  
  
 狀態圖表顯示，在多數的寫入與讀取作業之間，您必須呼叫其中一個位置函式：  
  
-   如果資料流的最後一個作業是寫入，您就不能呼叫讀取函式。  
  
-   如果資料流的最後一個作業是讀取，您就不能呼叫寫入函式，除非讀取作業設定了檔案結尾指標。  
  
 最後，狀態圖表顯示位置作業永遠不會減少後續可能發生的有效函式呼叫數。  
  
## <a name="see-also"></a>另請參閱  
 [檔案和資料流](../c-runtime-library/files-and-streams.md)
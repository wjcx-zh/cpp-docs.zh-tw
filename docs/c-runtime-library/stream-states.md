---
title: "資料流狀態 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "資料流, 狀態"
ms.assetid: 5f28c968-f132-403f-968c-8417ff315e52
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 資料流狀態
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

有效狀態和狀態轉換，以資料流如下圖所示。  
  
 ![資料流](../c-runtime-library/media/stream.png "stream")  
  
 每一個圓形表示穩定狀態。  每一行表示可能因函式呼叫在資料流的轉換。  函式的五個群組可能會造成狀態轉換。  
  
 前三個群組中的函式\<stdio.h\>中宣告:  
  
-   位元組讀取函式 —[fgetc](../c-runtime-library/reference/fgetc-fgetwc.md)、 [fgets](../c-runtime-library/reference/fgets-fgetws.md)、 [fread](../c-runtime-library/reference/fread.md)、 [fscanf](../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)、 [getc](../c-runtime-library/reference/getc-getwc.md)、 [getchar](../c-runtime-library/reference/getc-getwc.md)、 [gets](../c-runtime-library/gets-getws.md)、 [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)和 [ungetc](../c-runtime-library/reference/ungetc-ungetwc.md)  
  
-   位元組寫入函式 —[fprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)、 [fputc](../c-runtime-library/reference/fputc-fputwc.md)、 [fputs](../c-runtime-library/reference/fputs-fputws.md)、 [fwrite](../c-runtime-library/reference/fwrite.md)、 [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)、 [putc](../c-runtime-library/reference/putc-putwc.md)、 [putchar](../c-runtime-library/reference/putc-putwc.md)、 [puts](../c-runtime-library/reference/puts-putws.md)、 [vfprintf](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)和 [vprintf](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)  
  
-   位置函式 —[fflush](../c-runtime-library/reference/fflush.md)、 [fseek](../c-runtime-library/reference/fseek-fseeki64.md)、 [fsetpos](../c-runtime-library/reference/fsetpos.md)和 [rewind](../c-runtime-library/reference/rewind.md)  
  
 其餘兩群組中的函式在\<wchar.h\>宣告:  
  
-   寬讀取的函式 — [fgetwc](../c-runtime-library/reference/fgetc-fgetwc.md)、 [fgetws](../c-runtime-library/reference/fgets-fgetws.md)、 [fwscanf](../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)、 [getwc](../c-runtime-library/reference/getc-getwc.md)、 [getwchar](../c-runtime-library/reference/getc-getwc.md)、 [ungetwc](../c-runtime-library/reference/ungetc-ungetwc.md)和 [wscanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)，  
  
-   寬寫入函式 —[fwprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)、 [fputwc](../c-runtime-library/reference/fputc-fputwc.md)、 [fputws](../c-runtime-library/reference/fputs-fputws.md)、 [putwc](../c-runtime-library/reference/putc-putwc.md)、 [putwchar](../c-runtime-library/reference/fputc-fputwc.md)、 [vfwprintf](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)、 [vwprintf](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)和 [wprintf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)，  
  
 說明圖表指出您必須在大部分寫入和讀取作業之間呼叫其中一個的函式:  
  
-   若資料流的最後一個作業為寫入，則您不能讀取函式。  
  
-   若資料流的最後一個作業是否為唯讀，您不能呼叫函式寫入，除非該讀取作業設定檔案結尾指示器。  
  
 最後，狀態圖表表示是作業從未取消可以遵循有效函式呼叫的數目。  
  
## 請參閱  
 [檔案和資料流](../c-runtime-library/files-and-streams.md)
---
title: "文字和二進位模式的 Unicode 資料流 I/O | Microsoft Docs"
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
  - "I/O [CRT], Unicode 資料流"
  - "資料流 I/O 常式"
  - "Unicode 資料流 I/O"
  - "Unicode, 資料流 I/O 常式"
ms.assetid: 68be0c3e-a9e6-4fd5-b34a-1b5207f0e7d6
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 文字和二進位模式的 Unicode 資料流 I/O
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當 Unicode 資料流 I\/O 常式 \(例如 `fwprintf`、 `fwscanf`、 `fgetwc`、 `fputwc`、 `fgetws`或 `fputws`\) 上開啟於文字模式的檔案 \(預設值\)時，這兩種字元轉換發生:  
  
-   Unicode 對 MBCS 或是 MBCS 對 Unicode 的轉換。  當Unicode 資料流 I\/O 函式在文字模式下運作時，會假設來源或目的資料流是多位元組字元的序列。  因此，Unicode 資料流輸入函式會將多位元組字元轉換為寬字元 \(就像呼叫 `mbtowc` 函式一樣\)。  基於相同的原因，Unicode 資料流輸出函式會將寬字元轉換為多位元組字元 \(就像呼叫 `wctomb` 函式一樣\)。  
  
-   重設為一組 \(CR\-LF\) 轉譯。  這個轉譯在 MBCS – Unicode 轉換之前 \(Unicode 資料流輸入函式的\) 和 Unicode 對 MBCS 轉譯後 \(Unicode 資料流輸出的功能\)發生。  在輸入時，每組傳輸回傳都會重設為一組組合轉譯成單一新行字元。  在輸出時，每組傳輸回傳都會重設為一組組合轉譯成單一新行字元。  
  
 不過，當 Unicode 資料流 I\/O 函式在二進位模式時運作時，檔案會假設是 Unicode ，並且在輸入或輸出時，不會出現 CR\-LF 轉譯或字元轉換。  使用 \_setmode \(\_fileno \(stdin\)， \_O\_BINARY\)；指出要正確使用在 UNICODE 文字檔的 wcin。  
  
## 請參閱  
 [依分類區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)   
 [輸入和輸出](../c-runtime-library/input-and-output.md)
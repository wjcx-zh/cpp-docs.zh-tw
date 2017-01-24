---
title: "檔案讀取/寫入存取常數 | Microsoft Docs"
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
  - "c.constants.file"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "檔案讀取/寫入的存取常數"
  - "常數 [C++], 檔案屬性"
  - "檔案讀取/寫入存取常數"
  - "讀取/寫入存取常數"
  - "寫入存取常數"
ms.assetid: 56cd1d22-39a5-4fcf-bea2-7046d249e8ee
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 檔案讀取/寫入存取常數
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
  
#include <stdio.h>  
```  
  
## 備註  
 這些常數可指定存取檔案要求的型別 \(如「a」， 「r」或「w」\) 。  [平移模式](../c-runtime-library/file-translation-constants.md) \(「b」或「t」\) 和 [對磁碟模式](../c-runtime-library/commit-to-disk-constants.md) \(「c」或「n」\)都可依照存取類型指定。  
  
 存取型別如下。  
  
 **「a」**。  
 開啟以附加撰寫在檔案結尾；如果檔案不存在，請先建立檔案。  任何寫入作業都發生在檔案結尾。  雖然檔案指標可以使用`fseek`或 **rewind**重新調整位置，但是在執行任何寫入作業之前，指標永遠會移回至檔案結尾。  
  
 **"a\+"**。  
 與上面相同，但是也允許讀取。  
  
 **"r"**  
 開啟以讀取。  如果檔案不存在或找不到檔案，則開啟檔案的呼叫將會失敗。  
  
 **"r\+"**  
 開啟以進行讀取和寫入。  如果檔案不存在或找不到檔案，則開啟檔案的呼叫將會失敗。  
  
 **"w"**  
 開啟空白檔案以寫入。  如果指定的檔案已存在，其內容將被終結。  
  
 **"w\+"**  
 開啟空白檔案以進行讀取和寫入。  如果指定的檔案已存在，其內容將被終結。  
  
 當 "r\+", "w\+"或 "a\+"型別被指定為˙存取類型時，讀取和寫入將同時被允許 \(表示檔案是要開啟以供「更新」之用\)。  然而，在您在讀取和寫入之間切換時，必須有 `fflush`、 `fsetpos`、 `fseek` 或 **rewind** 作業的介入。  目前位置可以為 `fsetpos` 或 `fseek` 作業被指定。  
  
## 請參閱  
 [\_fdopen、\_wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)   
 [fopen、\_wfopen](../c-runtime-library/reference/fopen-wfopen.md)   
 [freopen、\_wfreopen](../c-runtime-library/reference/freopen-wfreopen.md)   
 [\_fsopen、\_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)   
 [\_popen、\_wpopen](../c-runtime-library/reference/popen-wpopen.md)   
 [全域常數](../c-runtime-library/global-constants.md)
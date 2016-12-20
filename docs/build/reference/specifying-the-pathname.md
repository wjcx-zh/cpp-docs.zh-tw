---
title: "指定路徑名稱 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe 編譯器, 輸出檔"
  - "名稱 [C++], 編譯器輸出檔案"
  - "輸出檔, 指定路徑名稱"
ms.assetid: 7a6595ce-3383-44ae-957a-466bfa29c343
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 指定路徑名稱
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

每一輸出檔選項會接受一個可以指定輸出檔位置和名稱的 *pathname* 引數。  這個引數可以包括磁碟機名稱、目錄和檔名。  選項與引數之間不可以有空格。  
  
 如果 *pathname* 包含一個檔名而沒有副檔名，編譯器將會對輸出賦予一個預設副檔名。  如果 *pathname* 包括一個目錄卻沒有檔名，編譯器會以預設名稱在指定的目錄中建立一個檔案。  預設名稱是依據原始程式檔的主檔名，再加上一個依據輸出檔類型的預設副檔名。  如果您完全不加 *pathname*，編譯器會以預設名稱在預設目錄中建立一個檔案。  
  
 另外，*pathname* 引數也可以是裝置名稱 \(AUX、CON、PRN 或 NUL\)，而不是檔案名稱。  不可在選項與裝置名稱之間使用空格，或以分號做為裝置名稱的一部分。  
  
|裝置名稱|表示|  
|----------|--------|  
|AUX|輔助裝置|  
|CON|主控台|  
|PRN|Printer|  
|NUL|Null 裝置 \(沒有建立檔案\)|  
  
## 範例  
 以下命令列會將對應檔傳送至印表機：  
  
```  
CL /FmPRN HELLO.CPP  
```  
  
## 請參閱  
 [輸出檔 \(\/F\) 選項](../../build/reference/output-file-f-options.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)
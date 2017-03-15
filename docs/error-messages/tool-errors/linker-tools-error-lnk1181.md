---
title: "連結器工具錯誤 LNK1181 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1181"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1181"
ms.assetid: 984b0db6-e331-4284-b2a7-a212fe96c486
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 連結器工具錯誤 LNK1181
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法開啟輸入檔 'filename'  
  
 連結器找不到 `filename`，因為它不存在或找不到路徑。  
  
 錯誤 LNK1181 部分常見的原因包括：  
  
-   在連結器列以其他相依性的方式參考 `filename`，但檔案不存在。  
  
-   缺少 **\/LIBPATH** 陳述式，以指定包含 `filename` 的目錄。  
  
 若要解決以上問題，請確定連結器列參考到的任何檔案都存在於系統，並確定包含連結器相依檔案的每個目錄各有一個 **\/LIBPATH** 陳述式。  
  
 可能造成 LNK1181 錯誤的另一個原因是：並未用引號括住有內嵌空格的長檔名。在此情況下，連結器將只能辨認檔名至第一個空格，然後假設檔案副檔名為 .obj。這種情況的解決方案是：用引號括住長檔名 \(路徑加上檔名\)。  
  
 如需詳細資訊，請參閱 [.lib 檔做為連結器輸入](../../build/reference/dot-lib-files-as-linker-input.md)。  
  
## 請參閱  
 [\/LIBPATH \(其他 Libpath\)](../../build/reference/libpath-additional-libpath.md)
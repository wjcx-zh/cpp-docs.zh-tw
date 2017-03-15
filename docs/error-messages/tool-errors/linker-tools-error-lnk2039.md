---
title: "連結器工具錯誤 LNK2039 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK2039"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2039"
ms.assetid: eaa296bd-4901-41f6-8410-6d03ee827144
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具錯誤 LNK2039
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

匯入在其他的 .obj 中定義的 ref 類別 '\<type\>'；應匯入或定義它，兩者擇一而非全部  
  
 ref 類別 '\<`type`\>' 中指定的 .obj 檔案匯入，但是也會在另一個 .obj 檔案裡定義。  這種情況可能會造成執行階段錯誤或其他未預期的行為。  
  
### 更正這個錯誤  
  
1.  檢查是否在另一個 .obj 檔案定義 '`type`'，並檢查是否必須從 .winmd 檔案匯入它。  
  
2.  移除定義或匯入。  
  
## 請參閱  
 [連結器工具錯誤和警告](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)   
 [連結器工具錯誤 LNK1332](../../error-messages/tool-errors/linker-tools-error-lnk1332.md)
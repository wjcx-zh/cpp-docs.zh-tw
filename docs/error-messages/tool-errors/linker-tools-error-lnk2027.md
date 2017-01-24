---
title: "連結器工具錯誤 LNK2027 | Microsoft Docs"
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
  - "LNK2027"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2027"
ms.assetid: e2f857a8-8e8a-4697-bbff-12ccb84a35c1
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具錯誤 LNK2027
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法解析的模組參考 'module'  
  
 傳遞至連結器的檔案在模組上有相依性，但既不是以 **\/ASSEMBLYMODULE** 指定，也不是直接傳遞給連結器。  
  
 若要解決 LNK2027，請執行下列任一種方法：  
  
-   不要傳遞給連結器具有模組相依性的檔案。  
  
-   以 **\/ASSEMBLYMODULE** 指定模組。  
  
-   如果模組是安全 .netmodule，請直接將模組傳遞給連結器。  
  
 如需詳細資訊，請參閱[\/ASSEMBLYMODULE \(將 MSIL 模組加入組件\)](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)與[.netmodule 檔做為連結器輸入](../../build/reference/netmodule-files-as-linker-input.md)。
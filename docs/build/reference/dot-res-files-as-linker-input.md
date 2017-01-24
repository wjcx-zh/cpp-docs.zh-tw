---
title: ".Res 檔做為連結器輸入 | Microsoft Docs"
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
  - ".res 檔做為連結器輸入"
  - "連結 [C++], 資源檔"
  - "RES 檔做為連結器輸入"
  - "資源檔, 連結"
ms.assetid: 9c37ab00-97df-4d9a-91cd-6bf132970683
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .Res 檔做為連結器輸入
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您可以在連結程式的時候指定 .res 檔。  .res 檔是由資源編譯器 \(RC\) 建立的。  LINK 會自動將 .res 檔轉換為 COFF。  CVTRES.exe 工具必須與 LINK.exe 在同一個目錄，或者是在 PATH 環境變數中指定的目錄。  
  
## 請參閱  
 [LINK 輸入檔](../../build/reference/link-input-files.md)   
 [連結器選項](../../build/reference/linker-options.md)
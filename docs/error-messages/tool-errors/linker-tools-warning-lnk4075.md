---
title: "連結器工具警告 LNK4075 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4075"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4075"
ms.assetid: f39ad3f9-c263-4cf0-9d70-259fc56ac96d
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 連結器工具警告 LNK4075
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

忽略 'option1'，由於 'option2' 規格  
  
 第二個選項會覆寫第一個選項。  
  
 正指定互斥 \(Mutually Exclusive\) 的連結器選項。檢查您的連結器選項。指定連結器選項之處是依您建置專案的方式而定。  
  
-   如果您是在開發環境中建置，請在專案的連結器屬性頁中尋找，查看這兩種連結器選項指定之處。如需詳細資訊，請參閱 [HOW TO：以屬性頁指定專案屬性](../../misc/how-to-specify-project-properties-with-property-pages.md)。  
  
-   如果您在命令列建置，請在該處查看所指定的連結器選項。  
  
-   如果是以建置指令碼建置，請搜查指令碼，查看這兩個連結器選項是在何處指定。  
  
 當您找到指定互斥的連結器選項之位置，請移除其中一個連結器選項。  
  
 下面是一些明確的實例：  
  
-   如果您連結以 **\/ZI** 編譯的模組，其中隱含內部連結器選項，稱為 \/EDITANDCONTINUE，和以 \/OPT:REF、\/OPT:ICF 或 \/INCREMENTAL:NO 編譯的模組，其中並未隱含 \/EDITANDCONTINUE，您將會接到 LNK4075 錯誤訊息。如需詳細資訊，請參閱[\/Z7、\/Zi、\/ZI \(偵錯資訊格式\)](../../build/reference/z7-zi-zi-debug-information-format.md)。
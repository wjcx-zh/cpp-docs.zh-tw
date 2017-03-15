---
title: "/DRIVER (Windows NT 核心模式驅動程式) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.driver"
  - "/driver"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/DRIVER 連結器選項"
  - "DRIVER 連結器選項"
  - "-DRIVER 連結器選項"
  - "核心模式驅動程式"
ms.assetid: aeee8e28-5d97-40f5-ba16-9f370fe8a1b8
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# /DRIVER (Windows NT 核心模式驅動程式)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/DRIVER[:UPONLY | :WDM]  
```  
  
## 備註  
 使用 \/DRIVER 連結器選項建置 Windows NT 核心模式驅動程式。  
  
 **\/DRIVER:UPONLY** 會使連結器將 **IMAGE\_FILE\_UP\_SYSTEM\_ONLY** 位元加到輸出標頭的特性中，以表示它是單一處理器 \(UP\) 驅動程式。  作業系統會拒絕將 UP 驅動程式載入到多處理器 \(MP\) 系統。  
  
 **\/DRIVER:WDM** 會使連結器設定選擇性標頭之 DllCharacteristics 欄位中的 **IMAGE\_DLLCHARACTERISTICS\_WDM\_DRIVER** 位元。  
  
 如果未指定 **\/DRIVER**，連結器就不會設定這些位元。  
  
 如果指定了 **\/DRIVER**：  
  
-   \/FIXED:NO 會作用 \([\/FIXED \(固定基底位址\)](../../build/reference/fixed-fixed-base-address.md)\)。  
  
-   輸出檔的副檔名將會是 .sys。  使用 **\/OUT** 變更預設檔案名稱和副檔名 \([\/OUT \(輸出檔名稱\)](../../build/reference/out-output-file-name.md)\)。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[**系統**\] 屬性頁。  
  
4.  修改 \[**驅動程式**\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 `P:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.driver`。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)
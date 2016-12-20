---
title: "/MACHINE (指定目標平台) | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.TargetMachine"
  - "/machine"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/MACHINE 連結器選項"
  - "MACHINE 連結器選項"
  - "-MACHINE 連結器選項"
  - "對應檔, 建立連結器"
  - "目標平台"
ms.assetid: 8d41bf4b-7e53-4ab9-9085-d852b08d31c2
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /MACHINE (指定目標平台)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/MACHINE:{ARM|EBC|X64|X86}  
```  
  
## 備註  
 \/MACHINE 選項會指定程式的目標平台。  
  
 通常，您不需指定 \/MACHINE 選項。  LINK 會從 .obj 檔推斷電腦類型。  不過，在某些情況下，LINK 會無法判斷電腦類型並且會發出[連結器工具錯誤 LNK1113](../../error-messages/tool-errors/linker-tools-error-lnk1113.md)。  如果發生這樣的錯誤訊息，請指定 \/MACHINE。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[**進階**\] 屬性頁。  
  
4.  修改 \[目標電腦\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TargetMachine%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)
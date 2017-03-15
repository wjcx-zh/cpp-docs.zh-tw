---
title: "/PGD (指定特性指引最佳化資訊庫) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.ProfileGuidedDatabase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/PGD 連結器選項"
  - "-PGD 連結器選項"
ms.assetid: 9f312498-493b-461f-886f-92652257e443
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# /PGD (指定特性指引最佳化資訊庫)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\/PGD：`filename`  
  
## 備註  
 其中：  
  
 `filename`  
 指定將用來存放有關執行程式之資訊的 .pgd 檔名稱。  
  
## 備註  
 使用 [\/LTCG:PGINSTRUMENT](../../build/reference/ltcg-link-time-code-generation.md) 時，使用 \/PGD 指定 .pgd 檔的非預設名稱或位置。  如果您不指定 \/PGD，.pgd 檔名將與輸出檔 \(.exe 或 .dll\) 名稱相同，並將建立在叫用連結的同一個目錄中。  
  
 使用 \/LTCG:PGOPTIMIZE 時，使用 \/PGD 指定 .pgd 檔的名稱，以便用來建立最佳化的影像。  
  
 如需詳細資訊，請參閱[特性指引最佳化](../../build/reference/profile-guided-optimizations.md)。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  展開 \[**組態屬性**\] 節點。  
  
3.  展開 **\[連結器\]** 節點。  
  
4.  按一下 \[**最佳化**\] 屬性頁。  
  
5.  修改 \[**特性指引資料庫**\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProfileGuidedDatabase%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)
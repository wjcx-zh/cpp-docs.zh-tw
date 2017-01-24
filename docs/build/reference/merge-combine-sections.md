---
title: "/MERGE (結合區段) | Microsoft Docs"
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
  - "/merge"
  - "VC.Project.VCLinkerTool.MergeSections"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/MERGE 連結器選項"
  - "MERGE 連結器選項"
  - "-MERGE 連結器選項"
  - "區段"
  - "區段, 組合"
  - "區段, 命名"
ms.assetid: 10fb20c2-0b3f-4c8d-98a8-f69aedf03d52
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /MERGE (結合區段)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/MERGE:from=to  
```  
  
## 備註  
 \/MERGE 選項會將第一個區段 \(*from*\) 與第二個區段 \(*to*\) 結合，並命名所產生的區段為 *to*。  例如 `/merge:.rdata=.text`。  
  
 如果第二個區段不存在，LINK 會將區段 *from* 重新命名為 *to*。  
  
 \/MERGE 選項對於建立 VxD 和覆寫編譯器產生的區段名稱而言，相當有用。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[進階\] 屬性頁。  
  
4.  修改 \[合併區段\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MergeSections%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)
---
title: "/PDBSTRIPPED (移除專用符號) | Microsoft Docs"
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
  - "/pdbstripped"
  - "VC.Project.VCLinkerTool.StripPrivateSymbols"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pdb 檔案, 移除私用符號"
  - "/PDBSTRIPPED 連結器選項"
  - "PDB 檔案, 移除私用符號"
  - "PDBSTRIPPED 連結器選項"
  - "-PDBSTRIPPED 連結器選項"
ms.assetid: 9b9e0070-6a13-4142-8180-19c003fbbd55
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /PDBSTRIPPED (移除專用符號)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/PDBSTRIPPED:pdb_file_name  
```  
  
## 備註  
 其中：  
  
 *pdb\_file\_name*  
 是使用者對連結器所建立移除專用符號的程式資料庫 \(PDB\) 所指定的名稱。  
  
## 備註  
 當您以任何會產生 PDB 檔的編譯器或連結器選項 \([\/DEBUG](../../build/reference/debug-generate-debug-info.md)、[\/Z7](../../build/reference/z7-zi-zi-debug-information-format.md)、\/Zd 或 \/Zi\) 建置程式影像時，\/PDBSTRIPPED 選項會建立第二個程式資料庫 \(PDB\) 檔。  第二個 PDB 檔會省略您不想要出貨給客戶的符號。  第二個 PDB 檔只會包含：  
  
-   公用符號  
  
-   目的檔清單以及它們所提供的可執行檔部分  
  
-   用來周遊堆疊的框架指標最佳化 \(FPO\) 偵錯記錄  
  
 移除專用符號的 PDB 不會包含：  
  
-   型別資訊  
  
-   行號資訊  
  
-   每一目的檔的 CodeView 符號 \(例如函式、區域及靜態資料的符號\)  
  
 當您使用 \/PDBSTRIPPED 時，仍然會產生完整的 PDB 檔。  
  
 如果您不建立 PDB 檔，\/PDBSTRIPPED 便會被忽略。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[偵錯\] 屬性頁。  
  
4.  修改 \[移除專用符號\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StripPrivateSymbols%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)
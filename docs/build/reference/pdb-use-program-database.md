---
title: "/PDB (使用程式資料庫) | Microsoft Docs"
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
  - "/pdb"
  - "VC.Project.VCLinkerTool.ProgramDatabaseFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pdb 檔案, 建立"
  - "/PDB 連結器選項"
  - "PDB 檔案, 建立"
  - "PDB 連結器選項"
  - "-PDB 連結器選項"
ms.assetid: d23db0ce-10cb-427a-bc60-d6b2a852723d
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /PDB (使用程式資料庫)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/PDB:filename  
```  
  
## 備註  
 其中：  
  
 *filename*  
 是使用者對連結器建立的程式資料庫 \(PDB\) 所指定的名稱。  它會取代預設的名稱。  
  
## 備註  
 依預設值，指定 [\/DEBUG](../../build/reference/debug-generate-debug-info.md) 之後，連結器便會建立一個存放偵錯資訊的程式資料庫 \(PDB\)。  這個 PDB 的預設檔名有程式的主檔名和副檔名 .pdb。  
  
 請使用 \/PDB:*filename* 指定 PDB 檔的名稱。  如果沒有指定 \/DEBUG，\/PDB 選項便會被忽略。  
  
 PDB 最大可達 2GB。  
  
 如需詳細資訊，請參閱 [.pdb 檔做為連結器輸入](../../build/reference/dot-pdb-files-as-linker-input.md)。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[偵錯\] 屬性頁。  
  
4.  修改 \[產生程式資料庫檔\] 屬性  
  
### 若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProgramDatabaseFile%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)
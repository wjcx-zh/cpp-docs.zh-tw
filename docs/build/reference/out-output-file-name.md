---
title: "/OUT (輸出檔名稱) | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.OutputFile"
  - "/out"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/OUT C++ 連結器選項"
  - "連結器 [C++], 輸出檔"
  - "OUT 連結器選項"
  - "-OUT 連結器選項"
  - "輸出檔, name 連結器選項"
ms.assetid: 976210a4-e51f-4cfb-af5e-c16344455834
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /OUT (輸出檔名稱)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/OUT:filename  
```  
  
## 備註  
 其中：  
  
 *filename*  
 是使用者指定的輸出檔名稱。  它會取代預設的名稱。  
  
## 備註  
 \/OUT 選項會覆寫連結器建立的程式預設名稱和位置。  
  
 依預設值，連結器會使用所指定的第一個 .obj 檔的主檔名和適當的副檔名 \(.exe 或 .dll\) 來組成檔案名稱。  
  
 這個選項會取代對應檔或匯入程式庫的預設主檔名。  如需詳細資訊，請參閱[產生對應檔](../../build/reference/map-generate-mapfile.md) \(\/MAP\) 和[\/IMPLIB](../../build/reference/implib-name-import-library.md)。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[一般\] 屬性頁。  
  
4.  修改 \[輸出檔\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)
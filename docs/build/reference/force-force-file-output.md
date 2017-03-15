---
title: "/FORCE (強制檔案輸出) | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.ForceLink"
  - "/force"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/FORCE 連結器選項"
  - "連結器中的檔案輸出"
  - "FORCE 連結器選項"
  - "-FORCE 連結器選項"
ms.assetid: b1e9a218-a5eb-4e60-a4a4-65b4be15e5da
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /FORCE (強制檔案輸出)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/FORCE:[MULTIPLE|UNRESOLVED]  
```  
  
## 備註  
 \/FORCE 選項是告訴連結器即使參考到一個未定義或多重定義的符號，也要建立一個有效的 .exe 檔或 DLL。  
  
 \/FORCE 選項可以接受選擇性 \(Optional\) 引數：  
  
-   不論 LINK 是否找到符號有一個以上的定義，使用 \/FORCE:MULTIPLE 都會建立輸出檔。  
  
-   不論 LINK 是否找到未定義的符號，使用 \/FORCE:UNRESOLVED 都會建立輸出檔。如果未解析進入點符號，則會忽略 \/FORCE:UNRESOLVED。  
  
 不加引數的 \/FORCE 意味著符號多次定義和未解析。  
  
 用這個選項所建立的檔案可能無法依預期狀況執行。  指定 \/FORCE 選項時連結器將不會以累加方式連結。  
  
 如果模組是以 **\/clr** 編譯，**\/FORCE** 將不會建立影像。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[**命令列**\] 屬性頁。  
  
4.  在 \[**其他選項**\] 方塊中輸入選項。  
  
### 若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)
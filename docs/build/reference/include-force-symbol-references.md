---
title: "/INCLUDE (強制符號參考) | Microsoft Docs"
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
  - "/include"
  - "VC.Project.VCLinkerTool.ForceSymbolReferences"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/INCLUDE 連結器選項"
  - "force symbol references 連結器選項"
  - "INCLUDE 連結器選項"
  - "-INCLUDE 連結器選項"
  - "符號參考連結器強制"
  - "符號, 加入至符號表"
ms.assetid: 4a039677-360a-480f-bd0b-448e239b449c
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /INCLUDE (強制符號參考)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/INCLUDE:symbol  
```  
  
## 備註  
 其中：  
  
 `symbol`  
 是要指定加入到符號表的符號。  
  
## 備註  
 \/INCLUDE 選項會告訴連結器將指定的符號加入至符號表。  
  
 若要指定多個符號，請在符號名稱間輸入一個逗號 \(,\)、分號 \(;\) 或者空格。  在命令列上，請對每一符號指定一次 \/INCLUDE:`symbol`。  
  
 連結器是將含有符號定義的目的檔加入到程式以解析 `symbol`。  如果要包括一個在其他情況下不會連結到程式的程式庫目的檔，這項功能就非常有用。  
  
 用這個選項指定符號會覆寫 [\/OPT:REF](../../build/reference/opt-optimizations.md) 對該符號的移除。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[輸入\] 屬性頁。  
  
4.  修改 \[強制符號參考\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ForceSymbolReferences%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)
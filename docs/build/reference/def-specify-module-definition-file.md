---
title: "/DEF (指定模組定義檔) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.ModuleDefinitionFile"
  - "/def"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/DEF 連結器選項"
  - "DEF 連結器選項"
  - "-DEF 連結器選項"
  - "模組定義檔"
  - "模組定義檔, 指定"
ms.assetid: 6497fa68-65f0-48ca-8f66-b87166fc631a
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# /DEF (指定模組定義檔)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/DEF:filename  
```  
  
## 備註  
 其中：  
  
 *filename*  
 是要傳遞給連結器的模組定義檔 \(.def\) 的名稱。  
  
## 備註  
 \/DEF 選項會將模組定義檔 \(.def\) 傳遞至連結器。  只能指定一個 .def 檔給 LINK。  如需有關 .def 檔的詳細資訊，請參閱[模組定義檔](../../build/reference/module-definition-dot-def-files.md)。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[輸入\] 屬性頁。  
  
4.  修改 \[模組定義檔\] 屬性。  
  
 若要從開發環境內指定 .def 檔，您應該將它與其他檔案一同加入至專案，然後將這個檔案指定到 \/DEF 選項。  
  
### 若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ModuleDefinitionFile%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)
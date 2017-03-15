---
title: "/LIBPATH (其他 Libpath) | Microsoft Docs"
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
  - "/libpath"
  - "VC.Project.VCLinkerTool.AdditionalLibraryDirectories"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/LIBPATH 連結器選項"
  - "Additional Libpath 連結器選項"
  - "環境程式庫路徑覆寫"
  - "LIBPATH 連結器選項"
  - "-LIBPATH 連結器選項"
  - "程式庫路徑連結器選項"
ms.assetid: 7240af0b-9a3d-4d53-8169-2a92cd6958ba
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /LIBPATH (其他 Libpath)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/LIBPATH:dir  
```  
  
## 備註  
 其中：  
  
 `dir`  
 是指定連結器在搜尋 LIB 環境選項中指定的路徑之前所要搜尋的路徑。  
  
## 備註  
 使用 \/LIBPATH 選項會覆寫環境程式庫路徑。  連結器會首先搜尋這個選項指定的路徑，然後再搜尋 LIB 環境變數中指定的路徑。  您輸入的每一個 \/LIBPATH 選項只能指定一個目錄。  如果您想要指定一個以上的目錄，您必須指定多個 \/LIBPATH 選項。  然後連結器便會依序搜尋指定的目錄。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[一般\] 屬性頁。  
  
4.  修改 \[其他程式庫目錄\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalLibraryDirectories%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)
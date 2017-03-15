---
title: "/NODEFAULTLIB (忽略程式庫) | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.IgnoreAllDefaultLibraries"
  - "VC.Project.VCLinkerTool.IgnoreDefaultLibraryNames"
  - "/nodefaultlib"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/NODEFAULTLIB 連結器選項"
  - "預設程式庫, 移除"
  - "略過程式庫連結器選項"
  - "程式庫, 略過"
  - "NODEFAULTLIB 連結器選項"
  - "-NODEFAULTLIB 連結器選項"
ms.assetid: 7270b673-6711-468e-97a7-c2925ac2be6e
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /NODEFAULTLIB (忽略程式庫)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/NODEFAULTLIB[:library]   
```  
  
## 備註  
 其中：  
  
 *library*  
 是您要連結器在解析外部參考時忽略的程式庫。  
  
## 備註  
 \/NODEFAULTLIB 選項會告訴連結器在解析外部參考時從它搜尋的程式庫清單中移除一或多個預設程式庫。  
  
 若要建立不包含預設程式庫參考的 .obj 檔，請使用 [\/Zl \(省略預設程式庫名稱\)](../../build/reference/zl-omit-default-library-name.md)。  
  
 依預設值，\/NODEFAULTLIB 會在解析外部參考時從它搜尋的程式庫清單中移除所有預設的程式庫。  選擇性參數 *library* 可以讓您在解析外部參考時從它搜尋的程式庫清單中移除一個或多個指定的程式庫。  請針對您要排除的每一程式庫指定一個 \/NODEFAULTLIB 選項。  
  
 連結器解析對外部定義參考的方式是首先搜尋您明確指定的程式庫，接著再搜尋以 \/DEFAULTLIB 選項指定的預設程式庫，然後再搜尋 .obj 檔中所命名的預設程式庫。  
  
 當兩者都指定了同樣的 *library* 名稱時，\/NODEFAULTLIB:*library* 會覆寫 [\/DEFAULTLIB:](../../build/reference/defaultlib-specify-default-library.md)*library*。  
  
 舉例來說，假設您使用 \/NODEFAULTLIB 建置您的程式而不使用 C 執行階段程式庫，您可能也必須使用 [\/ENTRY](../../build/reference/entry-entry-point-symbol.md) 以指定您程式中的進入點 \(函式\)。  如需詳細資訊，請參閱[CRT 程式庫功能](../../c-runtime-library/crt-library-features.md)。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[**輸入**\] 屬性頁。  
  
4.  選取 \[**忽略所有預設程式庫**\] 屬性，或指定您要在 \[**忽略特定程式庫**\] 屬性中忽略的程式庫清單。  \[**命令列**\] 屬性頁會顯示出您在這些屬性上所做變更的效果。  
  
### 若要以程式設計方式設定這個連結器選項  
  
-   請參閱<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreDefaultLibraryNames%2A>以及<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreAllDefaultLibraries%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)
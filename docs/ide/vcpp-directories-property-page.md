---
title: "VC++ 目錄屬性頁 | Microsoft Docs"
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
  - "VC.Project.VCDirectories.IncludePath"
  - "VC.Project.VCDirectories.ReferencePath"
  - "VC.Project.VCDirectories.SourcePath"
  - "VC.Project.VCDirectories.LibraryWPath"
  - "VC.Project.VCDirectories.ExecutablePath"
  - "VC.Project.VCDirectories.LibraryPath"
  - "VS.ToolsOptionsPages.Projects.VCDirectories"
  - "VC.Project.VCDirectories.ExcludePath"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VC++ 目錄屬性頁"
ms.assetid: 428eeef6-f127-4271-b3ea-0ae6f2c3d624
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# VC++ 目錄屬性頁
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定您要 Visual Studio 用來建置專案的目錄。  若要存取這個屬性頁，請在 \[**方案總管**\] 中，開啟專案的捷徑功能表並且選擇 \[**屬性**\]，然後在 \[**屬性頁**\] 對話方塊的左窗格中，展開 \[**組態屬性**\] 並選取 \[**VC\+\+ 目錄**\]。  
  
 當您使用 Visual Studio 建立專案時，將會繼承特定目錄。  其中許多值會以巨集呈現。  若要檢查巨集的目前值，請在 \[**VC\+\+ 目錄**\] 頁面的右窗格中選取資料列 \(例如，\[**Include 目錄**\]\)，選擇右邊的向下箭號按鈕，選擇 \[**編輯**\]，然後在顯示的對話方塊中，選擇 \[**巨集**\] 按鈕。  如需詳細資訊，請參閱這些部落格文章：[VC\+\+ 目錄](http://blogs.msdn.com/b/vsproject/archive/2009/07/07/vc-directories.aspx)、[繼承的屬性和屬性工作表](http://blogs.msdn.com/b/vsproject/archive/2009/06/23/inherited-properties-and-property-sheets.aspx)和 [Visual Studio 2010 C\+\+ 專案升級指南](http://blogs.msdn.com/b/vcblog/archive/2010/03/02/visual-studio-2010-c-project-upgrade-guide.aspx)。  
  
## 目錄類型  
 您也可以指定其他目錄，如下所示。  
  
 **可執行檔目錄**  
 要在其中搜尋可執行檔的目錄。  對應至 **PATH** 環境變數。  
  
 **Include 目錄**  
 要在其中搜尋原始程式碼中所參考之 Include 檔案的目錄。  對應至 **INCLUDE** 環境變數。  
  
 **參考目錄**  
 要在其中搜尋組件和模組 \(中繼資料\) 檔的目錄，原始程式碼是使用 [\#using](../preprocessor/hash-using-directive-cpp.md) 指示詞參考這些檔案。  對應至 **LIBPATH** 環境變數。  
  
 **程式庫目錄**  
 要在其中搜尋程式庫 \(.lib\) 檔案的目錄；包括執行階段程式庫。  對應至 **LIB** 環境變數。  此設定不適用於 .obj 檔案，若要連結 .obj 檔案，在[連結器](../ide/linker-property-pages.md)的 \[**一般**\] 屬性頁上，選取 \[**其他程式庫相依性**\]，然後指定檔案的相對路徑。  
  
 **來源目錄**  
 要在其中搜尋用於 IntelliSense 之來源檔的目錄。  
  
 **排除目錄**  
 檢查組建相依性時不會搜尋的目錄。  
  
#### 指定或修改目錄設定  
  
1.  在 \[**方案總管**\] 中開啟您所要變更專案的捷徑功能表，然後選擇 **\[屬性\]**。  
  
2.  在 \[**屬性頁**\] 對話方塊的左窗格中，展開 \[**組態屬性**\]，然後選取 \[**VC\+\+ 目錄**\]。  
  
3.  若要修改其中一個目錄清單，請選擇該清單，然後在右邊的向下箭號按鈕，選擇 \[**編輯**\]。  
  
     在顯示的對話方塊中，您可以加入或移除值，因此，您可以值出現的順序重新排列。  您也可以選擇或清除 \[**從父代或專案預設值繼承**\] 以變更專案是否會繼承任何設定。  
  
## 共用設定  
 您可以與其他使用者或多部電腦共用專案屬性。  如需詳細資訊，請參閱[使用專案屬性](../ide/working-with-project-properties.md)。  
  
## 請參閱  
 [使用專案屬性](../ide/working-with-project-properties.md)
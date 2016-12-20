---
title: "如何：將自訂工具整合至專案屬性中 | Microsoft Docs"
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
  - "msbuild.cpp.howto.integratecustomtools"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "msbuild (c++), 如何：整合自訂工具"
ms.assetid: f32d91a4-44e9-4de3-aa9a-1c7f709ad2ee
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 如何：將自訂工具整合至專案屬性中
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以建立基礎 XML 結構描述檔案，以將自訂工作選項加入至 Visual Studio 的 \[**屬性頁**\] 視窗。  
  
 \[**屬性頁**\] 視窗的 \[**組態屬性**\] 區段會顯示我們稱為「*規則*」\(Rule\) 的設定群組。  每個規則各包含某項工具或某組功能的設定。  例如，\[**連結器**\] 規則包含連結器工具的設定。  規則中的設定可以再細分為不同的「*分類*」\(Category\)。  
  
 本文件解釋如何在設定目錄中建立檔案，並讓該檔案包含您的自訂工具所需的屬性，以便在 Visual Studio 啟動時載入這些屬性。  如需如何修改檔案的詳細資訊，請在Visual Studio 專案小組部落格參閱 [平台 Extensibilty 第 2 部分](http://go.microsoft.com/fwlink/?LinkID=191489)。  
  
### 若要加入或變更專案屬性  
  
1.  在 XML 編輯器中建立 XML 檔案。  
  
2.  將檔案儲存在 %ProgramFiles%\\MSBuild\\Microsoft.Cpp\\v4.0\\ 資料夾中。  \[**屬性頁**\] 視窗中的每個規則都各以此資料夾中的某個 XML 檔案代表。  請確定檔案在資料夾中具有唯一的名稱。  
  
3.  複製 %ProgramFiles%\\MSBuild\\Microsoft.Cpp\\v4.0\\cl.xml 的內容，關閉它但不要儲存變更，然後將內容貼到新的 XML 檔案中。  您可以使用任何 XML 結構描述檔案 \- 這只是一個讓您有個地方可開始的範本檔案。  
  
4.  在新的 XML 檔案中，根據您的需求修改內容。  請務必變更檔案開頭的 **Rule Name** 和 **Rule.DisplayName**。  
  
5.  儲存變更並關閉檔案。  
  
6.  Visual Studio 啟動時會載入 %ProgramFiles%\\MSBuild\\Microsoft.Cpp\\v4.0\\ 中的 XML 檔案。  因此，為了測試新檔案，請重新啟動 Visual Studio。  
  
7.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下專案，然後按一下 \[**屬性**\]。  在 \[**屬性頁**\] 視窗的左窗格中，確認有一個新節點是以您的「規則」命名。  
  
## 請參閱  
 [MSBuild \(Visual C\+\+\)](../build/msbuild-visual-cpp.md)
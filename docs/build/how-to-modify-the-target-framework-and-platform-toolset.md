---
title: "如何：修改目標 Framework 和平台工具組 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
f1_keywords: 
  - "msbuild.cpp.howto.modifytargetframeworkandplatformtoolset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "msbuild (c++), 如何：修改目標 Framework 和平台工具組"
ms.assetid: 031b1d54-e6e1-4da7-9868-3e75a87d9ffe
caps.latest.revision: 32
caps.handback.revision: 32
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 如何：修改目標 Framework 和平台工具組
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以變更 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 專案設定，來設定不同的 .NET Framework 目標版本以及使用不同的平台工具組。 根據預設，專案系統會使用對應於建立專案所用 Visual Studio 版本的 .NET Framework 版本及工具組版本。 您可以修改專案屬性來變更目標平台工具組。 您可以修改專案 \(.vcxproj\) 檔案來變更目標 Framework。 您不必針對每個編譯目標維護一個不同的程式碼基底。  
  
> [!IMPORTANT]
>  部分版本可能不支援修改的目標 Framework 或平台工具組。 如需相容性資訊，請參閱 [移植、移轉和升級 Visual Studio 專案](../Topic/Porting,%20Migrating,%20and%20Upgrading%20Visual%20Studio%20Projects.md)。  
  
 當您變更目標 Framework 時，也會將平台工具組變更為支援該 Framework 的版本。 例如，若要使用 .NET Framework 4.5，必須使用 Visual Studio 2015 \(v140\)、Visual Studio 2013 \(v120\) 或 Visual Studio 2012 \(v110\) 這些相容的平台工具組。 您可以使用 \[**Windows7.1SDK**\] 平台工具組，將目標設定為 .NET Framework 2.0、3.0、3.5 和 4 以及 x86、Itanium 和 x64 平台。  
  
> [!NOTE]
>  若要變更目標平台工具組，您必須已經安裝相關聯的 Visual Studio 版本或 Windows Platform SDK。 例如，若要使用 **Windows7.1SDK** 平台工具組的 Itanium 平台，必須安裝[適用於 Windows 7 的 Windows SDK及 .NET Framework 4 SP1](http://www.microsoft.com/download/details.aspx?id=8279)；但您可以使用其他相容的 Visual Studio 版本執行開發工作，但前提是要使用正確的 Framework 版本及平台工具組。  
  
 您可以建立自訂平台工具組進一步擴充目標平台。 如需詳細資訊，請參閱 Visual C\+\+ 部落格中的 [C\+\+ 原生多目標](http://go.microsoft.com/fwlink/?LinkId=196619)。  
  
### 若要變更目標 Framework  
  
1.  在 Visual Studio 的**方案總管**中選取您的專案。 在功能表列上開啟 \[專案\] 功能表，然後選擇 \[卸載專案\]。 這會卸載專案的專案 \(.vcxproj\) 檔案。  
  
    > [!NOTE]
    >  在 Visual Studio 中修改專案檔時，無法載入 C \+\+ 專案。 不過，當專案在 Visual Studio 中載入時，您可以使用其他編輯器 \(例如記事本\) 修改專案檔。 Visual Studio 會偵測到專案檔已變更，並提示您重新載入專案。  
  
2.  在功能表列上，選取 \[**檔案**\]、\[**開啟**\]、\[**檔案**\]。 在 \[**開啟檔案**\] 對話方塊中，巡覽至專案資料夾，然後開啟專案 \(.vcxproj\) 檔案。  
  
3.  在專案檔中，尋找目標 Framework 版本的項目。 例如，如果您的專案設計為使用 .NET Framework 4.5，請在 `<TargetFrameworkVersion>v4.5</TargetFrameworkVersion>` 項目的 `<PropertyGroup Label="Globals">` 項目中找出 `<Project>`。 如果 `<TargetFrameworkVersion>` 項目不存在，您的專案不會使用 .NET Framework，也就不需要變更。  
  
4.  將值變更為所需的 Framwork 版本，例如 v3.5 或 v4.6。  
  
5.  儲存變更並關閉編輯器。  
  
6.  在 \[**方案總管**\]中，開啟專案的捷徑功能表，然後選擇 \[**重新載入專案**\]。  
  
7.  若要驗證此變更，請在 \[方案總管\] 上按一下滑鼠右鍵，以開啟專案 \(而非解決方案\) 的捷徑功能表，然後選擇 \[屬性\]，以開啟專案的 \[屬性頁\] 對話方塊。 在對話方塊的左窗格中，展開 \[**組態屬性**\]，然後選取 \[**一般**\]。 確認**目標 .NET Framework 版本**顯示的是新的  Framework 版本。  
  
### 若要變更專案工具組  
  
1.  在 Visual Studio 的 \[方案總管\] 中，開啟專案 \(而非解決方案\) 的捷徑功能表，然後選擇 \[屬性\] 以開啟專案 \[屬性頁\] 對話方塊。  
  
2.  在 \[**屬性頁**\] 對話方塊中，開啟 \[**組態**\] 下拉式清單，然後選取 \[**所有組態**\]。  
  
3.  在對話方塊的左窗格中，展開 \[**組態屬性**\]，然後選取 \[**一般**\]。  
  
4.  在右窗格中，選取 \[**平台工具組**\]，然後從下拉式清單中選取您想要的工具組。 例如，如果您已安裝 [!INCLUDE[vs_dev10_long](../build/includes/vs_dev10_long_md.md)] 工具組，請選取 \[Visual Studio 2010 \(v100\)\] 以用於您的專案。  
  
5.  選擇 \[**確定**\] 按鈕。  
  
## 請參閱  
 [MSBuild \(Visual C\+\+\)](../build/msbuild-visual-cpp.md)
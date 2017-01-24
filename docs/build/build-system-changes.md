---
title: "建置系統變更 | Microsoft Docs"
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
  - "vc.msbuild.changes"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "建置系統變更, $(Inherit)"
  - "建置系統變更, $(NoInherit)"
  - "建置系統變更, .vsprops"
  - "建置系統變更, 自訂建置規則"
  - "建置系統變更, MSBuild"
  - "建置系統變更, 專案檔 (.vcxprog)"
  - "MSBuild, 建置系統變更"
ms.assetid: e564d95f-a6cc-4d97-b57e-1a71daf66f4a
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 建置系統變更
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MSBuild 系統用於建置 Visual C\+\+ 專案。  不過，在 Visual Studio 2008 和較早版本使用 VCBuild 系統。  依賴 VCBuild 的某些檔案類型和概念不存在或表示不同於目前系統。  本文件將討論目前建置系統的差異。  
  
## .vcproj 現在改為 .vcxproj  
 專案檔不再使用 .vcproj 副檔名。  Visual Studio 會將舊版 Visual C\+\+ 建立的專案檔自動轉換為目前系統使用的格式。  如需如何手動升級專案的詳細資訊，請參閱 [\/Upgrade](../Topic/-Upgrade%20\(devenv.exe\).md)。  
  
 在目前版本中，專案檔的副檔名是 .vcxproj。  
  
## .vsprops 現在改為 .props  
 舊版中的「*專案屬性工作表*」\(Project Property Sheet\) 是 XML 架構檔案，而副檔名是 .vsprops。  專案屬性工作表可讓您指定建置工具 \(例如編譯器或連結器\) 的參數，以及建立使用者定義的巨集。  
  
 在目前版本中，專案屬性工作表的副檔名改為 .props。  
  
## 自訂建置規則和 .rules 檔  
 舊版中的「*規則檔*」\(Rule File\) 是 XML 架構檔案，而副檔名是 .rules。  規則檔可讓您定義自訂建置規則，並將這些規則加入 Visual C\+\+ 專案的建置流程中。  一種自訂建置規則，該規則可與一個或多個副檔名建立關聯，讓您將一個或多個輸入檔傳遞至可建立一個或多個輸出檔的工具。  
  
 在這個版本中，自訂建置規則是 .xml、.props 及 .targets 等三個檔案類型來呈現，而不是 .rules 檔案。  因此，在您將以舊版 Visual C\+\+ 建立的 .rules 檔案移轉到目前的版本時，會建立同等的 .xml、.props 及 .targets 檔案，並會將這些檔案和原始的 .rules 檔案一同儲存在專案中。  
  
> [!IMPORTANT]
>  在目前版本中， [!INCLUDE[TLA2#tla_ide](../build/includes/tla2sharptla_ide_md.md)] 不支援建立新規則。  因此，最簡單的方式就是使用以舊版 Visual C\+\+ 所建立之專案的規則檔會將專案移轉至目前版本。  
  
## 繼承巨集  
 在舊版中，**$\(Inherit\)** 巨集指定繼承的屬性出現在由專案建置系統所構成之命令列中的順序。  **$\(NoInherit\)** 巨集會造成 $\(Inherit\) 項目被忽略，因此應該被繼承的屬性沒有被繼承。  例如，依預設 $\(Inherit\) 巨集會導致以 [\/I \(其他 Include 目錄\)](../build/reference/i-additional-include-directories.md) 編譯器選項指定的檔案附加至命令列。  
  
 在目前版本中，是透過將屬性值指定為一個或多個常值和屬性巨集的串連形式，來支援繼承。  不支援 **$\(Inherit\)** 和 **$\(NoInherit\)** 巨集。  
  
 在下列範列中，會將以分號區隔的清單指派為屬性頁上的屬性。  此清單由 *\<value\>* 常值和 `MyProperty` 屬性的值串連而成，透過使用巨集標記法 **$\(***MyProperty***\)** 加以存取。  
  
```  
Property=<value>;$(MyProperty)  
```  
  
## .vcxproj.user 檔  
 使用者檔案 \(.vcxproj.user\) 用來儲存使用者專有的屬性，例如偵錯和部署設定。  vcxproj.user 檔案會套用至特定使用者的所有專案。  
  
## .vcxproj.filters 檔案  
 \[**方案總管**\] 是用來將檔案加入至專案，而篩選檔 \(.vcxproj.filters\) 則根據副檔名，定義在 \[**方案總管**\] 樹狀檢視的何處加入檔案。  
  
## VC\+\+ 目錄設定  
 Visual C\+\+ 目錄設定是在 [VC\+\+ 目錄屬性頁](../ide/vcpp-directories-property-page.md)上指定的。  在舊版的 Visual Studio 中，每位使用者可套用各自的目錄設定，且排除的目錄清單是指定於 sysincl.dat 檔案中。  
  
 如果您在命令列執行 [devenv \/resetsettings](../Topic/-ResetSettings%20\(devenv.exe\).md)，則無法變更 VC\+\+ 目錄設定。  如果您開啟 \[**工具**\] 功能表並按一下 \[**匯入和匯出設定**\]，然後再選取 \[**重設所有設定**\] 選項，也無法變更設定。  
  
 請使用以舊版 Visual C\+\+ 建立的 .vssettings 檔案移轉 VC\+\+ 目錄設定。  開啟 \[**工具**\] 功能表並按一下 \[**匯入和匯出設定**\]，選取 \[**匯入選取的環境設定**\]，然後遵循精靈中的指示。  或是在首次啟動 Visual Studio 時，選取 \[**選擇預設環境設定**\] 對話方塊中的 \[**從舊版移轉我的合適設定，並連同底下選取的預設值一起套用**\]。  
  
## 請參閱  
 [MSBuild \(Visual C\+\+\)](../build/msbuild-visual-cpp.md)
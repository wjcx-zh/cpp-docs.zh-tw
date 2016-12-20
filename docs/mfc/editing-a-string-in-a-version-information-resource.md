---
title: "Editing a String in a Version Information Resource | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.version"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "version information resources"
  - "resources [Visual Studio], editing version information"
ms.assetid: d3a7d4e4-7d31-47c2-902c-f50b8404ba4f
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Editing a String in a Version Information Resource
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### 編輯版本資訊資源內的字串  
  
1.  按一下並選取項目，然後再按一次開始編輯。 直接在版本資訊表或 [&#91;屬性&#93; 視窗](../Topic/Properties%20Window.md)中進行變更。 您所做的變更會反映在這兩個位置。  
  
     **注意** 在版本資訊編輯器中編輯 **FILEFLAGS** 機碼時，您會發現無法設定 .rc 檔的 **Debug**、**Private Build** 或 **Special Build** 屬性 \(位於 \[屬性\] 視窗中\)：  
  
    -   版本資訊編輯器會根據 **\_DEBUG** 組建旗標，利用資源指令碼中的 \#ifdef 來設定 **Debug** 屬性。  
  
    -   如果 **Private Build** 機碼在版本資訊表中已設定 \[值\]，則 **FILEFLAGS** 機碼的對應 **Private Build** 屬性 \(位於 \[屬性\] 視窗中\) 將會是 **True**。 如果 \[值\] 是空的，則該屬性為 **False**。 同樣地，**Special Build** 機碼 \(位於版本資訊表中\) 會繫結至 **FILEFLAGS** 機碼的 **Special Build** 屬性。  
  
 您可以按一下 \[機碼\] 或 \[值\] 欄位標題，來排序字串區塊的資訊順序。 這些標題會自動依照選取的順序重新排列資訊。  
  
 如需將資源加入 Managed 專案的相關資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。如需手動將資源檔加入 Managed 專案、存取資源、顯示靜態資源及指派資源字串給屬性的相關資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **需求**  
  
 Win32  
  
## 請參閱  
 [Version Information Editor](../mfc/version-information-editor.md)   
 [版本資訊 \(Windows\)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)
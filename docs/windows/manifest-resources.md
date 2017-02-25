---
title: "Manifest Resources | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "manifest resources"
  - "resources [Visual Studio], manifest"
ms.assetid: 8615334c-22a0-44c0-93e0-5924528c9917
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Manifest Resources
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

資訊清單資源是描述應用程式所用相依性的 XML 檔案。 例如，在 Visual Studio 中，MFC 精靈產生的資訊清單檔案會定義應用程式應該使用哪些 Windows 通用控制項 DLL \(5.0 或 6.0 版\)：  
  
```  
<description>Your app description here</description> <dependency> <dependentAssembly> <assemblyIdentity type="win32" name="Microsoft.Windows.Common-Controls" version="6.0.0.0" processorArchitecture="X86" publicKeyToken="6595b64144ccf1df" language="*" /> </dependentAssembly> </dependency>   
```  
  
 對於 Windows XP 或 Windows Vista 應用程式，資訊清單資源不只會指定應用程式使用最新版的 Windows 通用控制項 \(v6.0，如上所示\)，也會支援 [Syslink 控制項](http://msdn.microsoft.com/library/windows/desktop/bb760706)。  
  
 若要檢視資訊清單資源內含的版本和類型資訊，您可以在 XML 檢視器或在 Visual Studio [文字編輯器](http://msdn.microsoft.com/zh-tw/508e1f18-99d5-48ad-b5ad-d011b21c6ab1)中開啟此檔案。 如需詳細資訊，請參閱[在 Visual Studio 文字編輯器中開啟資訊清單資源](../windows/how-to-open-a-manifest-resource.md)。  
  
 如需將資源加入 Managed 專案的相關資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。如需手動將資源檔加入 Managed 專案、存取資源、顯示靜態資源及指派資源字串給屬性的相關資訊，請參閱[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 限制  
 每個模組只能有一個資訊清單資源。  
  
## 需求  
 Win32  
  
## 請參閱  
 [控制項](../mfc/controls-mfc.md)   
 [Working with Resource Files](../mfc/working-with-resource-files.md)
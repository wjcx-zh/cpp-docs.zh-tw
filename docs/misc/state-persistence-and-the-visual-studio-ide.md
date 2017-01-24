---
title: "狀態持續性和 Visual Studio IDE | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDE 設定, 狀態持續性"
  - "使用者設定 [Visual Studio SDK], 保存"
  - "工具選項頁 [Visual Studio SDK], 保存設定"
  - "IDE, 狀態持續性"
  - "持續性, 使用者設定"
ms.assetid: fdd49bb1-ed3b-4428-b685-de65c3215c1c
caps.latest.revision: 24
caps.handback.revision: 24
manager: "douge"
---
# 狀態持續性和 Visual Studio IDE
**匯入\/匯出設定**命令**工具**整合式的開發環境 \(IDE\) 的功能表匯入和匯出自訂的[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]環境。  [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]設定 Api 在[!INCLUDE[vsipsdk](../mfc/includes/vsipsdk_md.md)]啟用保存在使用者選擇時定義一或多個設定分類 \(狀態變數的群組\) 的 VSPackage **匯入\/匯出設定**指令。  
  
 GUID 唯一識別每個設定類別，並且定義於它自己的登錄項目，稱為 「 *自訂設定點*。  
  
> [!NOTE]
>  標準實作**工具選項**網頁、 **工具箱**，以及`Microsoft.VisualStudio.Shell.DialogPage`自動提供持續性的支援。  設定 API 可以覆寫預設的機制。  如需詳細資訊，請參閱 [擴充工具箱](../misc/extending-the-toolbox.md)、[選項頁](../misc/options-pages.md)和<xref:Microsoft.VisualStudio.Shell.DialogPage>。  
  
## 在本節中  
 [使用者設定的支援](../Topic/Support%20for%20User%20Settings.md)  
 說明的登錄設定 \(自訂設定點\) 及用來指定的屬性[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]指定的 VSPackage 所使用的設定實作。  
  
 [如何：使用 Interop 組件匯出設定](../misc/how-to-export-settings-by-using-interop-assemblies.md)  
 提供詳細的說明如何實作支援使用中儲存組態資料的[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]設定機制，interop 組件為基礎的 VSPackages。  
  
 [如何：使用 Interop 組件匯入設定](../misc/how-to-use-interop-assemblies-to-import-settings.md)  
 提供詳細的說明如何實作支援使用擷取組態資料的[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]設定機制，interop 組件為基礎的 VSPackages。  
  
 [匯出設定](../misc/exporting-settings.md)  
 詳細的說明，如何實作支援使用中儲存組態資料的[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]設定機制管理套件架構為基礎的 VSPackages。  
  
 [匯入設定](../misc/importing-settings.md)  
 提供詳細的說明如何實作支援使用擷取組態資料的[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]設定機制管理套件架構為基礎的 VSPackages。  
  
## 相關章節  
 [Working with Settings](http://msdn.microsoft.com/zh-tw/4c0a56ab-6091-4ebc-9dc7-52c40846bacb)  
 說明如何管理在 IDE 中匯出\/匯入的部份。  
  
 [選項頁](../misc/options-pages.md)  
 描述支援的[!INCLUDE[vsipsdk](../mfc/includes/vsipsdk_md.md)]會自動提供管理現有的或建立新的**工具選項**的網頁。  
  
 [擴充工具箱](../misc/extending-the-toolbox.md)  
 說明支援的[!INCLUDE[vsipsdk](../mfc/includes/vsipsdk_md.md)]會自動提供管理或延伸的**工具箱**。  
  
 [擴充使用者設定和選項](../Topic/Extending%20User%20Settings%20and%20Options.md)  
 說明如何設計您的 VSPackage，以取得與保留使用者喜好設定。
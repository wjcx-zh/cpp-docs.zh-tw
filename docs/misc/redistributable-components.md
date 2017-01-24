---
title: "可轉散發元件 | Microsoft Docs"
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
  - "可轉散發元件"
  - "安裝 [Visual Studio SDK], 可轉散發元件"
ms.assetid: 5072281f-3cb3-4985-bd93-c7981233bf92
caps.latest.revision: 20
caps.handback.revision: 20
manager: "douge"
---
# 可轉散發元件
[!INCLUDE[vsipsdk](../mfc/includes/vsipsdk_md.md)]包含程式碼，您可以發佈給洏峈根據規定[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] SDK 授權合約。  這類可轉散發的元件包括 Windows 安裝程式套件，並成為您的產品安裝過程中，部分合併模組和您編譯成您 VSPackages 的原始程式碼。  
  
 下表描述包含在可轉散發元件[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] SDK。  元件可以在中找到 *Visual Studio 的 SDK 的安裝路徑*\\VisualStudioIntegration\\Redistributables\\。  
  
|檔案名稱|描述|  
|----------|--------|  
|VSSDKTestHost.exe|您可以安裝這個可執行檔，為您安裝的一部分。|  
  
## 安裝可轉散發套件  
 安裝可執行程式碼的可轉散發元件作為 Windows Installer 封裝 \(.msi 檔案\)，以便 Microsoft 可以提供更新程式，如果有需要針對安全性弱點或其他重要的問題。  
  
 由於 Windows Installer 會允許安裝一次只能有一個套件，安裝可轉散發套件都需要您使用個別的可執行程式以循序方式安裝多個封裝。  這類的程式也常稱為 *chainer* 或*啟動載入器*。  
  
> [!IMPORTANT]
>  *巢狀安裝* \(也就是 *同時安裝*\)，建議在 Windows 安裝程式因為"巢狀 」 的產品無法安裝個別的補充程式。  它可以修補只能由已安裝它的產品。  因為[!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)]可轉散發套件將檔案安裝至共用的目錄，且必須支援獨立的修補程式、 沒有必須安裝使用巢狀的安裝。  
  
## 請參閱  
 [發行產品](../misc/releasing-a-visual-studio-integration-product.md)
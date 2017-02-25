---
title: "Custom Controls in the Dialog Editor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Custom Control"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controls [C++], templates"
  - "custom controls [Visual Studio], dialog boxes"
  - "custom controls [Visual Studio]"
  - "dialog box controls, custom (user) controls"
  - "Dialog editor, custom controls"
ms.assetid: f494b314-4000-4bbe-bbd0-4b18fb71ede1
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Custom Controls in the Dialog Editor
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

對話方塊編輯器讓您使用對話方塊範本中的現有「自訂」或「使用者」控制項。  
  
> [!NOTE]
>  這種方式的自訂控制項不會與 ActiveX 控制項搞混。  ActiveX 控制項有時稱為 OLE 自訂控制項。  此外，不要將這些控制項與 Windows 中的主控描繪控制項搞混。  
  
 這項功能是要讓您使用除了 Windows 提供之外的控制項。  在執行階段期間，控制項與視窗類別關聯 \(不同於 C\+\+ 類別\)。  完成相同工作的更常見方式是在您的對話方塊中安裝任何控制項，例如，靜態控制項。  然後於執行階段，在 [OnInitDialog](../Topic/CDialog::OnInitDialog.md) 函式中，移除此控制項並且以您的自訂控制項來取代。  
  
 這是舊技術。  現在會建議您撰寫 ActiveX 控制項或 Windows 通用控制項的子類別。  
  
 對於這些自訂控制項，您受限於：  
  
-   在對話方塊中設定位置。  
  
-   輸入標題。  
  
-   識別控制項的 Windows 類別名稱 \(您的應用程式程式碼必須根據這個名稱來登錄控制項\)。  
  
-   輸入設定控制項的式樣的 32 位元十六進位值。  
  
-   設定擴充式樣。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 需求  
 Win32  
  
## 請參閱  
 [Controls in Dialog Boxes](../mfc/controls-in-dialog-boxes.md)   
 [控制項](../mfc/controls-mfc.md)
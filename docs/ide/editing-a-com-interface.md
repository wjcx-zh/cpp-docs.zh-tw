---
title: "編輯 COM 介面 | Microsoft Docs"
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
  - "vc.codewiz.com.editing.interfaces"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COM 介面, 編輯"
  - "方法 [C++], 加入至 COM 介面"
  - "屬性 [C++], 加入至 COM 介面"
ms.assetid: 6c2909e0-af2d-4a37-bb39-ed372e6129cf
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 編輯 COM 介面
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可使用 \[類別檢視\] 捷徑功能表的命令，為 Visual C\+\+ 專案中的 COM 介面定義新的方法和屬性。  除此之外，您可從 \[工具箱\] 為 ActiveX 控制項定義事件。  
  
 至於 ATL 和 MFC 架構 COM 物件類別，您可在編輯介面的同時編輯類別實作 \(Implementation\)。  
  
> [!NOTE]
>  針對您在 \[加入類別\] 對話方塊以外定義的介面，Visual C\+\+ 會將方法或屬性加入至 .idl 檔案，同時，即使介面是手動加入的，也會將 Stub 加入至實作方法的類別。  
  
 下列三個精靈將幫助您自訂現有的介面。  您可從 \[類別檢視\] 中使用它們：  
  
|精靈|專案類型|  
|--------|----------|  
|[加入屬性精靈](../ide/names-add-property-wizard.md)|支援 ATL 的 ATL 或 MFC 專案。  以滑鼠右鍵按一下要加入屬性的介面。<br /><br /> Visual C\+\+ 會先偵測專案類型，並依據專案類型修改加入屬性精靈中的選項：<br /><br /> -   針對使用 [MFC 應用程式精靈](../mfc/reference/mfc-application-wizard.md)建立的專案中的分配介面 \(Dispinterface\) 而言，叫用 \(Invoke\) 加入屬性精靈會提供 MFC 特定的選項。<br />-   針對 MFC ActiveX 控制項介面，加入屬性精靈會提供內建方法 \(Stock Method\) 和內建屬性 \(Stock Property\) 的清單來提供您使用或自訂。<br />-   至於所有其他的介面，\[加入屬性精靈\] 在多數情況下會提供有用的選項。|  
|[加入方法精靈](../ide/add-method-wizard.md)|支援 ATL 的 ATL 或 MFC 專案。  以滑鼠右鍵按一下要加入方法的介面。<br /><br /> Visual C\+\+ 會先偵測專案類型，並依據專案類型修改加入方法精靈中的選項：<br /><br /> -   針對使用 [MFC 應用程式精靈](../mfc/reference/mfc-application-wizard.md)建立的專案中的分配介面而言，叫用加入方法精靈會提供 MFC 特定的選項。<br />-   針對 MFC ActiveX 控制項介面，加入方法精靈會提供內建方法和內建屬性的清單來提供您使用或自訂。<br />-   至於所有其他的介面，\[加入方法\] 精靈在多數情況下會提供有用的選項。|  
  
 除此之外，您可以藉由在 \[類別檢視\] 中以滑鼠右鍵按一下物件的控制項類別，以及按一下[實作介面](../ide/implement-interface-wizard.md)，在 COM 控制項上實作新的介面。  
  
## 請參閱  
 [Working with Resource Files](../mfc/working-with-resource-files.md)   
 [使用程式碼精靈加入功能](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Visual C\+\+ 專案類型](../ide/visual-cpp-project-types.md)
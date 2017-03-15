---
title: "建立 COM 介面 (Visual C++) | Microsoft Docs"
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
  - "vc.codewiz.com.creating.interfaces"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COM 介面, 建立"
ms.assetid: 1be84d3c-6886-4d1e-8493-56c4d38a96d4
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 建立 COM 介面 (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 提供精靈和樣板來為您的 COM 物件和 Automation 類別 \(Class\) 建立使用 COM 定義介面和分配介面的專案。  
  
 您可以使用這些精靈來執行下列三種常見的工作：  
  
-   [將 ATL 支援加入至 MFC 專案](../mfc/reference/adding-atl-support-to-your-mfc-project.md)  
  
     在您使用 [MFC 應用程式精靈](../mfc/reference/mfc-application-wizard.md)建立 MFC 專案之後，請將 ATL 支援加入至 MFC 應用程式，然後執行將 ATL 支援加入至 MFC 程式碼精靈。  這個支援只適用於加入至 MFC 可執行檔或 DLL 專案中的簡單 COM 物件。  這些 ATL 物件可有多個介面。  
  
-   [建立 MFC ActiveX 控制項](../mfc/reference/creating-an-mfc-activex-control.md)  
  
     開啟 [MFC ActiveX 控制項精靈](../mfc/reference/mfc-activex-control-wizard.md)來建立 ActiveX 控制項，並在 .idl 檔案和控制項類別中分別定義分配介面 \(Dispinterface\) 和事件對應。  
  
-   [加入 ATL 控制項](../atl/reference/adding-an-atl-control.md)  
  
     結合 [ATL 專案精靈](../atl/reference/atl-project-wizard.md)和 [ATL 控制項精靈](../atl/reference/atl-control-wizard.md)來建立 ATL ActiveX 控制項。  
  
     您也可以將 ATL 控制項加入至已加入 ATL 支援的 MFC 專案，就像前面描述的一樣。  除此之外，如果您選取 \[加入類別\] 對話方塊中的 \[**ATL 控制項**\]，而且尚未將 ATL 支援加入至 MFC 專案，則 Visual Studio 會顯示對話方塊來確定是否將 ATL 支援加入至 MFC 專案。  
  
     這個精靈會在專案類別中產生 IDL 來源和 COM 對應。  
  
 開啟 ATL 專案之後，[加入類別](../ide/add-class-dialog-box.md)對話方塊會讓您選擇其他精靈和範本，來將 COM 介面加入專案。  下列精靈允許您為物件建立一或多個介面：  
  
-   [ATL COM\+ 1.0 元件精靈](../atl/reference/atl-com-plus-1-0-component-wizard.md)  
  
-   [ATL 簡單物件精靈](../atl/reference/atl-simple-object-wizard.md)  
  
-   [ATL Active Server Page 元件精靈](../atl/reference/atl-active-server-page-component-wizard.md)  
  
-   [ATL 控制項精靈](../atl/reference/atl-control-wizard.md)  
  
 除此之外，您可以藉由在 \[類別檢視\] 中以滑鼠右鍵按一下物件的控制項類別，以及按一下[實作介面](../ide/implement-interface-wizard.md)，在 COM 控制項上實作新的介面。  
  
> [!NOTE]
>  Visual Studio 並不提供將介面加入專案的精靈。  您可使用 [ATL 簡單物件精靈](../atl/reference/atl-simple-object-wizard.md)加入簡單物件，以便將介面加入至 ATL 專案或[將 ATL 支援加入至 MFC 專案](../mfc/reference/adding-atl-support-to-your-mfc-project.md)。  除此之外，也可開啟專案的 .idl 檔，然後輸入下列程式碼來建立介面：  
  
```  
interface IMyInterface {  
};  
  
```  
  
 如需詳細資訊，請參閱[實作介面](../ide/implementing-an-interface-visual-cpp.md)和[將物件和控制項加入至 ATL 專案](../atl/reference/adding-objects-and-controls-to-an-atl-project.md)。  
  
 Visual C\+\+ 提供幾種方式來檢視和[編輯 COM 介面](../ide/editing-a-com-interface.md)，而這些 COM 介面是為您的專案所定義。  [類別檢視](http://msdn.microsoft.com/zh-tw/8d7430a9-3e33-454c-a9e1-a85e3d2db925)會顯示在 C\+\+ 專案的 .idl 檔中定義的任何介面或分配介面的圖示。  
  
 對 ATL 架構的 COM 物件類別來說，\[類別檢視\] 會讀取 ATL 類別中的 COM 對應，顯示 ATL 類別與其實作的任何介面之間的關聯性 \(Relationship\)。  
  
 在 \[類別檢視\] 和其捷徑功能表中，您可利用下列方式來使用介面：  
  
-   將 ATL 物件加入至 MFC 架構應用程式。  
  
-   加入方法、屬性及事件。  
  
-   按兩下項目來直接跳至項目的介面程式碼。  
  
## 請參閱  
 [使用應用程式精靈建立桌面專案](../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [使用程式碼精靈加入功能](../ide/adding-functionality-with-code-wizards-cpp.md)
---
title: "建立 COM 介面 （Visual c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.com.creating.interfaces
dev_langs: C++
helpviewer_keywords: COM interfaces, creating
ms.assetid: 1be84d3c-6886-4d1e-8493-56c4d38a96d4
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e7b5820686c3e6f01c37cbf527d0e631e5bcc25c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="creating-a-com-interface-visual-c"></a>建立 COM 介面 (Visual C++)
Visual c + + 提供精靈與範本建立的定義 COM 介面和分配介面使用 COM 物件與 automation 類別的專案。  
  
 您可以使用這些精靈來執行下列三個一般工作：  
  
-   [將 ATL 支援新增至 MFC 專案](../mfc/reference/adding-atl-support-to-your-mfc-project.md)  
  
     將 ATL 支援加入 MFC 應用程式之後您建立 MFC 專案使用, [MFC 應用程式精靈](../mfc/reference/mfc-application-wizard.md)，然後執行**將 ATL 支援加入至 MFC**程式碼精靈。 這項支援只適用於簡單的 COM 物件加入至 MFC 可執行檔或 DLL 專案。 這些 ATL 物件可能有多個介面。  
  
-   [建立 MFC ActiveX 控制項](../mfc/reference/creating-an-mfc-activex-control.md)  
  
     開啟[MFC ActiveX 控制項精靈](../mfc/reference/mfc-activex-control-wizard.md)dispinterface 與事件對應中的.idl 檔案和控制項類別中，分別定義建立 ActiveX 控制項。  
  
-   [新增 ATL 控制項](../atl/reference/adding-an-atl-control.md)  
  
     使用的組合[ATL 專案精靈](../atl/reference/atl-project-wizard.md)和[ATL 控制項精靈](../atl/reference/atl-control-wizard.md)建立 ATL ActiveX 控制項。  
  
     您也可以加入 ATL 控制項已加入 ATL 支援的 MFC 專案 （如上所述）。 此外，如果您選取**ATL 控制項**中**加入類別**對話方塊中，而且您有尚未加入 ATL 支援加入 MFC 專案，Visual Studio 會顯示對話方塊，確認將 ATL 支援加入至您MFC 專案。  
  
     這個精靈會產生 IDL 來源和 COM 對應專案類別中。  
  
 一旦開啟，ATL 專案[加入類別](../ide/add-class-dialog-box.md) 對話方塊可讓您選擇的其他精靈和範本加入至專案的 COM 介面。 下列精靈可讓您建立物件的一個或多個介面：  
  
-   [ATL COM+ 1.0 元件精靈](../atl/reference/atl-com-plus-1-0-component-wizard.md)  
  
-   [ATL 簡單物件精靈](../atl/reference/atl-simple-object-wizard.md)  
  
-   [ATL Active Server Page 元件精靈](../atl/reference/atl-active-server-page-component-wizard.md)  
  
-   [ATL 控制項精靈](../atl/reference/atl-control-wizard.md)  
  
 此外，實作新介面 COM 控制項上按一下滑鼠右鍵在 類別檢視物件的控制項類別，[實作介面](../ide/implement-interface-wizard.md)。  
  
> [!NOTE]
>  Visual Studio 不提供精靈，以將介面加入至專案。 您可以加入介面至 ATL 專案或[將 ATL 支援加入至 MFC 專案](../mfc/reference/adding-atl-support-to-your-mfc-project.md)加入簡單的物件，使用[ATL 簡單物件精靈](../atl/reference/atl-simple-object-wizard.md)。 或者，開啟專案的.idl 檔案，並建立介面中輸入：  
  
```  
interface IMyInterface {  
};  
  
```  
  
 請參閱[實作介面](../ide/implementing-an-interface-visual-cpp.md)和[將物件和控制項加入 ATL 專案](../atl/reference/adding-objects-and-controls-to-an-atl-project.md)如需詳細資訊。  
  
 Visual c + + 提供數種方式檢視和[編輯 COM 介面](../ide/editing-a-com-interface.md)定義您的專案。 [類別檢視](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925)顯示的任何介面或 dispinterface，用以在 c + + 專案中的.idl 檔案中定義的圖示。  
  
 Atl COM 物件的類別，類別檢視讀取 ATL 類別，以顯示 ATL 類別和它所實作的介面之間的關聯性中的 COM 對應。  
  
 在 類別檢視和其捷徑功能表中，您可以使用介面，如下所示：  
  
-   將 ATL 物件加入至 MFC 為基礎的應用程式。  
  
-   加入方法、 屬性和事件。  
  
-   來直接跳至的項目介面程式碼項目上按兩下。  
  
## <a name="see-also"></a>請參閱  
 [使用應用程式精靈建立桌面專案](../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [使用程式碼精靈加入功能](../ide/adding-functionality-with-code-wizards-cpp.md)
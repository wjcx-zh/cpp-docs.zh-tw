---
title: 使用程式碼精靈 （c + +） 加入功能 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.classes
dev_langs:
- C++
helpviewer_keywords:
- code wizards [C++]
- wizards [C++], code
- Visual C++ projects, adding functionality
- projects [C++], adding functionality
- class wizards [C++]
ms.assetid: 6afb7ef9-7056-423d-b244-91bb4236d1d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 55a2bb282d19a48cfd510056e327e7abca4de4ad
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="adding-functionality-with-code-wizards-c"></a>使用程式碼精靈 （c + +） 加入功能
當您建立專案之後時，您會想要變更或加入至該專案的功能。 這類工作包含建立新的類別，加入新的成員函式和變數，並加入 Automation 方法與屬性。 程式碼精靈被為了讓您執行所有這些作業。  
  
> [!NOTE]
>  您現在可以加入訊息處理常式和訊息對應到它們，並覆寫 MFC 使用的虛擬函式[屬性 視窗](/visualstudio/ide/reference/properties-window)。  
  
## <a name="accessing-visual-c-code-wizards"></a>存取 Visual c + + 程式碼精靈  
 有三個位置，您可以在其中存取 Visual c + + 程式碼精靈：  
  
-   在**專案**功能表上，**加入新項目**命令可讓您顯示`Add New Item`對話方塊，可協助您將新檔案加入您的專案。 **加入類別**命令便會顯示[加入類別](../ide/add-class-dialog-box.md)對話方塊中，依序開啟每個類別的類型與您要精靈可以將它加入至專案。 **加入資源**命令便會顯示[加入資源](../windows/add-resource-dialog-box.md)對話方塊中，您可以建立或選取要加入至專案的資源。  
  
     如果您反白顯示的類別或介面類別檢視 中的專案中**專案**功能表也會顯示下列命令：  
  
    -   **實作介面**（從僅限控制項類別）  
  
    -   **Add 函式**  
  
    -   **加入變數**  
  
    -   **加入連接點**（僅限 ATL 類別）  
  
    -   **將方法加入**（從僅限介面）  
  
    -   **將屬性加入**（從僅限介面）  
  
    -   **加入事件**（從僅限控制項類別）  
  
-   在**方案總管 中**，以滑鼠右鍵按一下任何資料夾，再按一下**新增**從捷徑功能表，讓您加入新的或現有的檔案、 多個資料夾、 項目、 類別、 資源，以及 Web 參考專案。  
  
-   從[類別檢視 視窗](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925)，以滑鼠右鍵按一下適當的節點，再按一下**新增**從捷徑功能表，讓您新增函式、 變數、 類別、 屬性、 方法、 事件、 介面、連接點或其他程式碼加入您的專案。  
  
    > [!NOTE]
    >  Visual Studio 不提供精靈，以將介面加入至專案。 您可以加入介面至 ATL 專案或[將 ATL 支援加入至 MFC 專案](../mfc/reference/adding-atl-support-to-your-mfc-project.md)加入簡單的物件，使用[ATL 簡單物件精靈](../atl/reference/atl-simple-object-wizard.md)。 或者，開啟專案的.idl 檔案，並建立介面中輸入：  
  
    ```  
    interface IMyInterface {  
    };  
  
    ```  
  
     請參閱[實作介面](../ide/implementing-an-interface-visual-cpp.md)和[將物件和控制項加入 ATL 專案](../atl/reference/adding-objects-and-controls-to-an-atl-project.md)如需詳細資訊。  
  
    |存取程式碼精靈|描述|  
    |-----------------------------|-----------------|  
    |加入新項目|加入新項目程式碼精靈會加入您的專案中的原始程式檔。 如有必要，其他目錄會建立包含專案的建置引擎希望找出這些解決方案的檔案。 加入項目圖示中可用的程式碼精靈包含：<br /><br /> 新增 c + + 原始程式檔 （.cpp、.h、.idl、.rc、.srf、.def、.rgs）。<br />新增 Web 開發檔案.html、.asp、.css （.xml）。<br />新增公用程式和資源檔，.bmp、.cur、.ico、.rct、.sql （.txt）。<br /><br /> 這些程式碼精靈通常不要求您的任何資訊，但將檔案加入您的開發樹狀目錄。 您可以重新命名屬性視窗中的檔案。|  
    |底下提供說明，包括方案總管|可從 [方案總管] 中的程式碼精靈取決於您將游標焦點所在的項目上按一下滑鼠右鍵。 如果**新增**選項不會顯示，當您以滑鼠右鍵按一下項目，將游標向上一層開發樹狀結構，並再試一次。 程式碼精靈會一律將額外的程式碼中的適當位置中開發樹狀目錄中，不論游標所在位置。 從 [方案總管] 中可用的程式碼精靈包含：<br /><br /> 加入類別 (開啟**加入類別**對話方塊包含新的程式碼精靈)。<br />新增資源 (新增、 匯入或自訂)。<br />新增 Web 參考。|  
    |類別檢視|類別檢視中可用的程式碼精靈取決於您將游標焦點所在時您以滑鼠右鍵按一下項目。 如果**新增**選項不會顯示，當您以滑鼠右鍵按一下項目，然後將游標向上一層中類別樹狀目錄，然後再試一次。 程式碼精靈會一律將額外的程式碼中的適當位置中開發樹狀目錄中，不論游標所在位置。 從 類別檢視可用的程式碼精靈包含：<br /><br /> -   [加入成員函式](../ide/adding-a-member-function-visual-cpp.md)。<br />-   [加入成員變數](../ide/adding-a-member-variable-visual-cpp.md)。<br />-   [將類別加入](../ide/adding-a-class-visual-cpp.md)。<br />-   [實作介面](../ide/implement-interface-wizard.md)（從僅限控制項類別）<br />-   [加入連接點](../ide/implement-connection-point-wizard.md)（僅限 ATL 類別）<br />-   [將方法加入](../ide/add-method-wizard.md)（從僅限介面）<br />-   [將屬性加入](../ide/names-add-property-wizard.md)（從僅限介面）<br />-   [加入事件](../ide/add-event-wizard.md)（從僅限控制項類別）<br /><br /> 選取 加入類別開啟**加入類別**對話方塊中，所有新的加入類別程式碼精靈可讓您存取。|  
  
## <a name="see-also"></a>另請參閱  
 [覆寫虛擬函式](../ide/overriding-a-virtual-function-visual-cpp.md)   
 [巡覽類別結構](../ide/navigating-the-class-structure-visual-cpp.md)   
 [使用應用程式精靈建立桌面專案](../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Visual c + + 專案類型](../ide/visual-cpp-project-types.md)   
 [為 Visual C++ 專案建立的檔案類型](../ide/file-types-created-for-visual-cpp-projects.md)
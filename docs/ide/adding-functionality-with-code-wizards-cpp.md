---
title: "使用程式碼精靈加入功能 | Microsoft Docs"
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
  - "vc.codewiz.classes"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "類別精靈 [C++]"
  - "程式碼精靈 [C++]"
  - "專案 [C++], 加入功能"
  - "Visual C++ 專案, 加入功能"
  - "精靈 [C++], 程式碼"
ms.assetid: 6afb7ef9-7056-423d-b244-91bb4236d1d7
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用程式碼精靈加入功能
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

一旦建立專案，您會想要變更或加入專案的功能。  這些工作包含建立新類別 \(Class\)、加入新的成員 \(Member\) 函式和變數以及加入 Automation 方法和屬性。  程式碼精靈就是設計來讓您進行這些工作。  
  
> [!NOTE]
>  您現在可使用[屬性視窗](../Topic/Properties%20Window.md)來加入訊息處理常式 \(Message Handler\)，並將訊息對應至它們並覆寫 MFC 虛擬函式 \(Virtual Function\)。  
  
## 存取 Visual C\+\+ 程式碼精靈  
 您可以從三個位置存取 Visual C\+\+ 程式碼精靈：  
  
-   \[**專案**\] 功能表的 \[**加入新項目**\] 命令允許開啟 \[`Add New Item`\] 對話方塊，幫助您將新檔案加入至專案中。  \[加入類別\] 命令會顯示[加入類別](../ide/add-class-dialog-box.md)對話方塊，接著就會為每個可加入專案的類別型別開啟精靈。  \[**加入資源**\] 命令則會顯示[加入資源](../windows/add-resource-dialog-box.md)對話方塊，您可從這裡建立或選取要加入至專案的資源。  
  
     如果在類別檢視中反白顯示您專案中的類別或介面，\[專案\] 功能表也會顯示下列命令：  
  
    -   **實作介面** \(僅限控制項類別\)  
  
    -   **加入函式**  
  
    -   **加入變數**  
  
    -   **加入連接點** \(僅限 ATL 類別\)  
  
    -   **加入方法** \(僅限介面\)  
  
    -   **加入屬性** \(僅限介面\)  
  
    -   **加入事件** \(僅限控制項類別\)  
  
-   在 \[**方案總管**\] 中以滑鼠右鍵按一下任何資料夾，接著從捷徑功能表按一下 \[**加入**\]，這會允許您將新的或現有檔案、更多資料夾、項目、類別、資源及 Web 參考加入至專案中。  
  
-   從[類別檢視視窗](http://msdn.microsoft.com/zh-tw/8d7430a9-3e33-454c-a9e1-a85e3d2db925)以滑鼠右鍵按一下適當節點，接著從捷徑功能表按一下 \[加入\]，這會允許您將函式、變數、類別、屬性、方法、事件、介面、連接點 \(Connection Point\) 或其他程式碼加入至專案中。  
  
    > [!NOTE]
    >  Visual Studio 並不提供將介面加入專案的精靈。  您可使用 [ATL 簡單物件精靈](../atl/reference/atl-simple-object-wizard.md)加入簡單物件，以便將介面加入至 ATL 專案或[將 ATL 支援加入至 MFC 專案](../mfc/reference/adding-atl-support-to-your-mfc-project.md)。  除此之外，也可開啟專案的 .idl 檔，然後輸入下列程式碼來建立介面：  
  
    ```  
    interface IMyInterface {  
    };  
  
    ```  
  
     如需詳細資訊，請參閱[實作介面](../ide/implementing-an-interface-visual-cpp.md)和[將物件和控制項加入至 ATL 專案](../atl/reference/adding-objects-and-controls-to-an-atl-project.md)。  
  
    |存取程式碼精靈的位置|描述|  
    |----------------|--------|  
    |加入新項目|加入新項目程式碼精靈會將原始程式檔加入至專案中。  必要時會建立其他目錄來包含專案組建引擎需要的檔案。  可從 \[加入項目\] 圖示使用的程式碼精靈包含：<br /><br /> -   加入 C\+\+ 原始程式檔 \(.cpp、.h、.idl、.rc、.srf、.def、.rgs\)。<br />-   加入 Web 開發檔案 \(.html、.asp、.css、.xml\)。<br />-   加入公用程式和資源檔 \(.bmp、.cur、.ico、.rct、.sql、.txt\)。<br /><br /> 這些程式碼精靈通常不會向您詢問任何資訊，但會將檔案加入至開發樹狀結構中。  您可在屬性視窗中重新命名這個檔案。|  
    |方案總管|\[方案總管\] 中，程式碼精靈的可用與否端視您以滑鼠右鍵按一下項目時的游標焦點 \(Focus\) 所在而定。  如果當您以滑鼠右鍵按一下項目時未出現 \[加入\] 選項，則請將游標移至開發樹狀結構的上一層並再試一次。  無論游標位置在哪，程式碼精靈都會將其他程式碼置於開發樹狀結構的適當位置。  \[方案總管\] 中可用的程式碼精靈包含：<br /><br /> -   加入類別 \(開啟包含新程式碼精靈的 \[**加入類別**\] 對話方塊\)。<br />-   加入資源 \(新增、匯入或自訂\)。<br />-   加入 Web 參考。|  
    |類別檢視|類別檢視中可用的程式碼精靈端視您以滑鼠右鍵按一下項目時的游標焦點所在而定。  如果當您以滑鼠右鍵按一下項目時未出現 \[加入\] 選項，則請將游標移至類別樹狀結構的上一層並再試一次。  無論游標位置在哪，程式碼精靈都會將其他程式碼置於開發樹狀結構的適當位置。  類別檢視中可用的程式碼精靈包含：<br /><br /> -   [加入成員函式](../ide/adding-a-member-function-visual-cpp.md)。<br />-   [加入成員變數](../ide/adding-a-member-variable-visual-cpp.md)。<br />-   [加入類別](../ide/adding-a-class-visual-cpp.md)。<br />-   [實作介面](../ide/implement-interface-wizard.md) \(僅限控制項類別\)<br />-   [加入連接點](../ide/implement-connection-point-wizard.md) \(僅限 ATL 類別\)<br />-   [加入方法](../ide/add-method-wizard.md) \(僅限介面\)<br />-   [加入屬性](../ide/names-add-property-wizard.md) \(僅限介面\)<br />-   [加入事件](../ide/add-event-wizard.md) \(僅限控制項類別\)<br /><br /> 選取 \[加入類別\] 會開啟 \[加入類別\] 對話方塊，讓您能夠存取所有新的加入類別程式碼精靈。|  
  
## 請參閱  
 [覆寫 Virtual 函式](../ide/overriding-a-virtual-function-visual-cpp.md)   
 [巡覽類別結構](../ide/navigating-the-class-structure-visual-cpp.md)   
 [使用應用程式精靈建立桌面專案](../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Visual C\+\+ 專案類型](../ide/visual-cpp-project-types.md)   
 [為 Visual C\+\+ 專案建立的檔案類型](../ide/file-types-created-for-visual-cpp-projects.md)
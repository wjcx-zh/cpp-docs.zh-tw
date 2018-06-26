---
title: 文件檢視架構的替代方案 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- documents [MFC], applications without
- CDocument class [MFC], space requirements
- views [MFC], applications without
ms.assetid: 2c22f352-a137-45ce-9971-c142173496fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1b99d8fb82b014fc2221f1ec1c0e6ad08ee75b4c
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930283"
---
# <a name="alternatives-to-the-documentview-architecture"></a>文件/檢視架構的替代方案
MFC 應用程式通常使用文件/檢視架構管理資訊、檔案格式以及對使用者的資料視覺呈現。 對於大部分的桌面應用程式，文件/檢視架構是適當且有效率的應用程式架構。 這種架構會將資料與檢視分開，而且在大部分情況下，可簡化您的應用程式並減少冗餘碼。  
  
 不過，文件/檢視架構在某些情況下並不適用。 請考慮下列範例：  
  
-   如果您要移植使用 C 針對 Windows 撰寫的應用程式，建議您先完成移植，再於應用程式中加入文件/檢視支援。  
  
-   如果您要撰寫輕量型公用程式，您可能會發現不需要使用文件/檢視架構即可進行。  
  
-   如果您的原始程式碼已經混用資料管理與資料檢視，那麼就不值得將程式碼移至文件/檢視模型，因為您必須將兩者分開。 您可能寧願將程式碼保持原狀。  
  
 若要建立不使用文件/檢視架構的應用程式，請清除**文件/檢視架構支援**MFC 應用程式精靈的步驟 1 中的核取方塊。 請參閱[MFC 應用程式精靈](../mfc/reference/mfc-application-wizard.md)如需詳細資訊。  
  
> [!NOTE]
>  MFC 應用程式精靈所產生的對話方塊架構應用程式不會使用與文件/檢視架構，所以**文件/檢視架構支援**核取方塊已停用，如果您選取對話方塊應用程式類型。  
  
 Visual C++ 精靈以及原始檔和對話方塊編輯器都可處理產生的應用程式，就如同處理任何其他精靈產生的應用程式一般。 應用程式可以支援工具列、 捲軸和狀態列，並具有**有關**方塊。 您的應用程式將不會登錄任何文件範本，而且不會包含文件類別。  
  
 請注意，產生的應用程式的檢視類別`CChildView`、 衍生自`CWnd`。 MFC 會在您的應用程式所建立的框架視窗內建立及定位一個檢視類別的執行個體。 MFC 仍然會強制使用檢視視窗，因為它可簡化應用程式內容的定位和管理作業。 您可以將繪製程式碼加入至這個類別的 `OnPaint` 成員。 您的程式碼應該將捲軸加入檢視中，而不是加入至框架。  
  
 由於 MFC 提供的文件/檢視架構負責實作許多應用程式的基本功能，因此如果專案中缺少它，表示您必須負責實作應用程式的許多重要功能：  
  
-   MFC 應用程式精靈所提供，只包含您的應用程式的功能表**新增**和**結束**命令**檔案**功能表。 (**新增**命令僅支援 MDI 應用程式，沒有文件/檢視表的 SDI 應用程式的支援。)產生的功能表資源將不支援 MRU (最近使用的) 清單。  
  
-   您必須加入處理常式函式和實作您的應用程式將支援，包括任何命令**開啟**和**儲存**上**檔案**功能表。 MFC 通常會提供程式碼來支援這些功能，不過，該支援與文件/檢視架構密切相關。  
  
-   應用程式的工具列 (如果您要求的話) 將會是最小。  
  
 強烈建議您使用「MFC 應用程式精靈」建立應用程式，而不要使用文件/檢視架構，因為精靈能夠保證產生正確的 MFC 架構。 不過，如果您必須避免使用精靈，以下提供幾種方法可在程式碼中略過文件/檢視架構：  
  
-   將文件當做未使用的附加項，並且在檢視類別中實作您的資料管理程式碼，如上面所建議。 文件的額外負荷會將對較低。 單一[CDocument](../mfc/reference/cdocument-class.md)物件會造成少量的額外負荷，加上的少量負荷`CDocument`的基底類別、 [CCmdTarget](../mfc/reference/ccmdtarget-class.md)和[CObject](../mfc/reference/cobject-class.md)。 後面兩個類別都很小。  
  
     在宣告`CDocument`:  
  
    -   兩個 `CString` 物件。  
  
    -   三個**BOOL**s。  
  
    -   一個 `CDocTemplate` 指標。  
  
    -   一個 `CPtrList` 物件，包含文件檢視的清單。  
  
     此外，文件需要一些時間來建立文件物件、其檢視物件、框架視窗及文件範本物件。  
  
-   將文件和檢視都當做未使用的附加項。 將資料管理和繪圖程式碼放入框架視窗中，而不是檢視中。 這個方法與 C 語言程式設計模型較接近。  
  
-   覆寫 MFC 架構中建立文件和檢視的部分，就可以完全排除建立它們。 文件建立程序是從呼叫 `CWinApp::AddDocTemplate` 開始。 請從應用程式類別的 `InitInstance` 成員函式中排除該呼叫，並且改成在 `InitInstance` 中自行建立框架視窗。 將資料管理程式碼放入框架視窗類別中。 在文件/檢視建立程序如下所示[文件/檢視建立](../mfc/document-view-creation.md)。 雖然這樣做多了一些工作並且需要對架構有更深入的了解，但是卻可以完全排除文件/檢視的額外負荷。  
  
 發行項[MFC： 使用資料庫類別不具文件和檢視表](../data/mfc-using-database-classes-without-documents-and-views.md)資料庫應用程式的內容中提供更具體的範例，文件/檢視的替代項目。  
  
## <a name="see-also"></a>另請參閱  
 [文件/檢視架構](../mfc/document-view-architecture.md)


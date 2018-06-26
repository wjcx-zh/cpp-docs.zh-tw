---
title: 表單檢視 (MFC) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- user interfaces [MFC], forms
- forms [MFC]
- applications [MFC], forms-based
- forms-based applications [MFC]
- forms [MFC], adding to applications
ms.assetid: efbe73c1-4ca4-4613-aac2-30d916e92c0e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8a717ca80d84b884014a2567228829ffd87c5178
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930296"
---
# <a name="form-views-mfc"></a>表單檢視 (MFC)
您可以將表單加入支援 MFC 程式庫，包括任何 Visual c + + 應用程式[表單架構應用程式](../mfc/reference/creating-a-forms-based-mfc-application.md)(其中的檢視類別衍生自`CFormView`)。 如果沒有一開始建立您的應用程式，以支援表單，Visual c + + 會將這項支援您，當您插入新的表單。 SDI 或 MDI 應用程式中，它會實作預設[文件/檢視架構](../mfc/document-view-architecture.md)，當使用者選擇**新增**命令 (根據預設，在**檔案**功能表)，VisualC + + 會提示使用者選擇從可用的表單。  
  
 在 SDI 應用程式，當使用者選擇**新增**命令時，表單的目前執行個體繼續執行，但如果找不到建立具有所選表單的應用程式的新執行個體。 MDI 應用程式中，表單的目前執行個體繼續執行，當使用者選擇**新增**命令。  
  
> [!NOTE]
>  您可以將表單插入對話方塊架構應用程式 (其對話方塊類別為基礎的一個`CDialog`，另一個類別實作的任何檢視中)。 不過，不具有文件/檢視架構中，Visual c + + 不會自動實作**檔案**&#124;**新增**功能。 您必須建立方法，讓使用者檢視其他形式，例如，藉由實作索引標籤式的對話方塊具有各種屬性頁。  
  
 當您將新的表單插入您的應用程式時，Visual c + + 會執行下列動作：  
  
-   建立類別，根據您選擇的格式樣式類別的其中一個 (`CFormView`， `CRecordView`， `CDaoRecordView`，或`CDialog`)。  
  
-   建立對話方塊資源具有適當的樣式 （或您可以使用尚未與類別相關聯的現有對話方塊資源）。  
  
     如果您選擇現有的對話方塊資源，您可能需要使用 [屬性] 頁面對話方塊來設定這些樣式。 必須包含 [樣式] 對話方塊：  
  
     **WS_CHILD**= On  
  
     **WS_BORDER**= 關閉  
  
     **WS_VISIBLE**= 關閉  
  
     **WS_CAPTION =** 關閉  
  
 應用程式的文件/檢視架構，**新表單**命令 （在類別檢視中按一下滑鼠右鍵） 也：  
  
-   建立`CDocument`-基礎類別  
  
     您不需要建立新的類別，您可以使用任何現有`CDocument`-基礎專案中的類別。  
  
-   產生的文件範本 (衍生自`CDocument`) 與字串、 功能表和圖示的資源。  
  
     您也可以建立新範本當成基底類別。  
  
-   將呼叫加入`AddDocumentTemplate`應用程式中`InitInstance`程式碼。  
  
     Visual c + + 加入此程式碼，為您建立時，這會將表單加入可用的表單清單，當使用者選擇每個新表單**新增**命令。 這個程式碼包含表單的相關聯的資源識別碼和相關聯的文件、 檢視和框架類別一起構成新的表單物件的名稱。  
  
     文件範本做為文件、 框架視窗和檢視之間的連線。 單一文件，您可以建立許多範本。  
  
 如需詳細資訊，請參閱:  
  
-   [建立表單架構應用程式](../mfc/reference/creating-a-forms-based-mfc-application.md)  
  
-   [將表單插入專案中](../mfc/inserting-a-form-into-a-project.md)  
  
## <a name="see-also"></a>另請參閱  
 [使用者介面項目](../mfc/user-interface-elements-mfc.md)

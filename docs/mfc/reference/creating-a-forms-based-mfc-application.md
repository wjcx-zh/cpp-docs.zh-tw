---
title: 建立表單架構的 MFC 應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfcforms.project
dev_langs:
- C++
helpviewer_keywords:
- applications [MFC], forms-based
- forms-based applications [MFC]
ms.assetid: 048d2f7d-b60d-4386-ad8e-71d49af9c05e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a5ee588d7fe90e5bfc39aa8e4ab7a7499b62ad98
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33372443"
---
# <a name="creating-a-forms-based-mfc-application"></a>建立表單架構的 MFC 應用程式
表單是讓使用者存取，並盡可能地變更資料的控制項的對話方塊。 若要開發應用程式中使用者選取 從選取的表單。 一般而言，表單架構應用程式可以讓使用者存取表單按一下**新增**從**檔案**功能表。 對話方塊架構應用程式，這並不提供使用者存取**新增**選項**檔案**功能表上，也會被視為表單架構應用程式。  
  
 單一文件介面 (SDI)，表單架構應用程式可讓特定的格式執行一次只有一個執行個體。 可以藉由選取新的表單，從 SDI 表單架構應用程式從執行不同的形式同時**新增**選項**檔案**功能表。  
  
 如果您建立多個文件介面 (MDI) 表單為基礎的應用程式，應用程式可以支援多個執行個體相同的格式。  
  
 如果您建立具有多個最上層文件支援的應用程式，桌面是隱含的父文件和文件的框架不會套用至應用程式的工作區。 您可以開啟文件中，每個都有它自己的畫面格、 功能表和工作列圖示的多個執行的個體。 您可以分別，關閉後續的執行個體的文件，但如果您選取`Exit`選項**檔案**關閉所有執行個體的初始執行個體，應用程式的功能表。  
  
 SDI、 MDI 和多個最上層文件應用程式是表單架構，並使用文件/檢視架構。  
  
 任何對話方塊架構的應用程式，根據定義，是為基礎。 對話方塊架構應用程式不使用的文件/檢視架構，因此您必須管理建立和存取方法的其他表單。  
  
 表單架構應用程式的基底類別是[CFormView](../../mfc/reference/cformview-class.md)。 如果您的應用程式具有資料庫支援，則您也可以選取任何類別衍生自`CFormView`。 表單是衍生自任何視窗`CFormView`或從任何類別繼承自`CFormView`。  
  
 即使您使用的基底類別，例如[CView](../../mfc/reference/cview-class.md)，您可以稍後再進行應用程式由表單型[加入 MFC 類別](../../mfc/reference/adding-an-mfc-class.md)衍生自`CFormView`和檢查**產生 DocTemplate資源**中的核取方塊[MFC 類別精靈](../../mfc/reference/document-template-strings-mfc-add-class-wizard.md)。  
  
 一旦您完成精靈，您的專案隨即開啟，而且選取`CFormView`(或類別繼承自`CFormView`) 為您的基底類別，或如果您建立對話方塊架構應用程式時，Visual c + + 開啟對話方塊編輯器。 此時，您已經備妥要設計您第一種形式。  
  
### <a name="to-begin-creating-a-forms-based-mfc-executable"></a>若要開始建立表單架構 MFC 可執行檔  
  
1.  請遵照[建立 MFC 應用程式](../../mfc/reference/creating-an-mfc-application.md)。  
  
2.  在 MFC 應用程式精靈[應用程式類型](../../mfc/reference/application-type-mfc-application-wizard.md)頁面上，選取**文件/檢視架構支援**核取方塊。  
  
3.  選取**單一文件**，**多份文件**，或**多個最上層文件**。  
  
    > [!NOTE]
    >  如果您選擇的 SDI、 MDI 或多個最上層文件介面應用程式，根據預設，`CView`設為您的應用程式中檢視的基底類別[產生的類別](../../mfc/reference/generated-classes-mfc-application-wizard.md)精靈頁面。 若要建立表單架構應用程式，您必須選取`CFormView`做為應用程式檢視的基底類別。 請注意，精靈會提供任何列印支援表單架構應用程式。  
  
4.  其他的精靈頁面上，設定您想要的任何其他專案選項。  
  
5.  按一下**完成**產生基本架構應用程式。  
  
 如需詳細資訊，請參閱:  
  
-   [衍生的檢視類別](../../mfc/derived-view-classes-available-in-mfc.md)  
  
-   [文件/檢視架構的替代方案](../../mfc/alternatives-to-the-document-view-architecture.md)  
  
-   [應用程式設計選擇](../../mfc/application-design-choices.md)  
  
## <a name="see-also"></a>另請參閱  
 [MFC 應用程式精靈](../../mfc/reference/mfc-application-wizard.md)   
 [表單檢視](../../mfc/form-views-mfc.md)   
 [建立檔案總管樣式的 MFC 應用程式](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)   
 [建立網頁瀏覽器樣式的 MFC 應用程式](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)


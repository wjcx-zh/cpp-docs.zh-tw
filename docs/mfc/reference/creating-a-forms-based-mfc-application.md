---
title: 建立表單架構的 MFC 應用程式
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfcforms.project
helpviewer_keywords:
- applications [MFC], forms-based
- forms-based applications [MFC]
ms.assetid: 048d2f7d-b60d-4386-ad8e-71d49af9c05e
ms.openlocfilehash: 6810a6c7fce91865a92d048129da29305e22abc1
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57291245"
---
# <a name="creating-a-forms-based-mfc-application"></a>建立表單架構的 MFC 應用程式

表單是包含控制項，可讓使用者存取，並盡可能地變更資料的對話方塊。 若要開發應用程式使用者從表單內的選取。 通常，表單為基礎的應用程式可以讓使用者存取表單按一下**的新**從**檔案**功能表。 對話方塊架構應用程式，不會不讓使用者存取權**的新**選項**檔案** 功能表中，也會被視為表單為基礎的應用程式。

單一文件介面 (SDI)，表單架構應用程式可讓特定的表單，以執行一次只有一個執行個體。 可以藉由選取新的表單，從 SDI 表單架構應用程式從執行不同的形式同時**的新**選項**檔案**功能表。

如果您要建立多重文件介面 (MDI) 表單為基礎的應用程式，應用程式將能夠支援多個相同的格式執行個體。

如果您建立具有多個最上層文件支援的應用程式，桌面是隱含的父文件和文件的框架不限於工作區的應用程式。 您可以開啟文件中，每個都有它自己的畫面格、 功能表和工作列圖示的多個執行的個體。 您可以個別關閉文件的後續執行個體，但如果您選取**結束**選項**檔案**初始執行個體，應用程式的功能表關閉所有執行個體。

SDI、 MDI 和多個最上層文件的應用程式是所有的表單架構，並使用文件/檢視架構。

任何對話方塊架構的應用程式，根據定義，是為基礎。 對話方塊架構應用程式不使用文件/檢視架構，因此您必須管理您自己的其他形式的建立和存取方法。

表單架構應用程式的基底類別是[CFormView](../../mfc/reference/cformview-class.md)。 如果您的應用程式具有資料庫的支援，則您也可以選取任何類別都衍生自`CFormView`。 表單是衍生自任何視窗`CFormView`或從任何類別都繼承自`CFormView`。

即使您使用的基底類別，例如[CView](../../mfc/reference/cview-class.md)，您可以稍後再進行您的應用程式的表單型[加入 MFC 類別](../../mfc/reference/adding-an-mfc-class.md)衍生自`CFormView`並檢查**產生 DocTemplate資源**中的核取方塊[MFC 類別精靈](../../mfc/reference/document-template-strings-mfc-add-class-wizard.md)。

一旦您完成精靈時，會開啟您的專案，以及您選取`CFormView`(或類別繼承自`CFormView`) 為您的基底類別，或如果您建立對話方塊架構應用程式時，Visual c + + 會開啟對話方塊編輯器。 此時，您已準備好設計您第一種形式。

### <a name="to-begin-creating-a-forms-based-mfc-executable"></a>若要開始建立表單型 MFC 可執行檔

1. 請遵照[建立 MFC 應用程式](../../mfc/reference/creating-an-mfc-application.md)。

1. 在 MFC 應用程式精靈[應用程式類型](../../mfc/reference/application-type-mfc-application-wizard.md)頁面上，選取**文件/檢視架構支援**核取方塊。

1. 選取 **單一文件**，**多份文件**，或**多個最上層的文件**。

    > [!NOTE]
    >  如果您選擇的 SDI、 MDI 或多個最上層文件介面應用程式，根據預設，`CView`設定為您的應用程式 檢視中的基底類別[產生的類別](../../mfc/reference/generated-classes-mfc-application-wizard.md)精靈頁面。 若要建立表單架構應用程式，您必須選取`CFormView`做為應用程式的檢視的基底類別。 請注意，精靈不提供列印支援表單架構應用程式。

1. 在精靈的其他頁面上設定您想要的任何其他專案選項。

1. 按一下 **完成**產生基本架構的應用程式。

如需詳細資訊，請參閱:

- [衍生的檢視類別](../../mfc/derived-view-classes-available-in-mfc.md)

- [文件/檢視架構的替代方案](../../mfc/alternatives-to-the-document-view-architecture.md)

- [應用程式設計選擇](../../mfc/application-design-choices.md)

## <a name="see-also"></a>另請參閱

[MFC 應用程式精靈](../../mfc/reference/mfc-application-wizard.md)<br/>
[表單檢視](../../mfc/form-views-mfc.md)<br/>
[建立檔案總管樣式的 MFC 應用程式](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)<br/>
[建立網頁瀏覽器樣式的 MFC 應用程式](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)

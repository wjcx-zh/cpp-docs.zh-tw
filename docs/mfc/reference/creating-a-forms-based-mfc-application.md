---
title: 建立表單架構的 MFC 應用程式
ms.date: 09/09/2019
f1_keywords:
- vc.appwiz.mfcforms.project
helpviewer_keywords:
- applications [MFC], forms-based
- forms-based applications [MFC]
ms.assetid: 048d2f7d-b60d-4386-ad8e-71d49af9c05e
ms.openlocfilehash: 1dbbc5c29f85ced846cb3e07a02a5d6a55c94b20
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908047"
---
# <a name="creating-a-forms-based-mfc-application"></a>建立表單架構的 MFC 應用程式

表單是一個對話方塊，其中包含可讓使用者存取和可能變更資料的控制項。 您可能想要開發一個應用程式，使用者可以在其中選取表單。 通常，以表單為基礎的應用程式可讓使用者**從 [檔案**] 功能表按一下 [**新增**] 來存取表單。 以對話方塊為基礎的應用程式（不提供使用者**在 [檔案**] 功能表中的**新**選項存取權）也會被視為以表單為基礎的應用程式。

單一檔介面（SDI）以表單為基礎的應用程式，一次只允許一個特定表單的實例執行。 您可以**從 [檔案] 功能表中**的 [**新增**] 選項選取新的表單，同時從 SDI 表單架構應用程式執行不同的表單。

如果您建立多重文件介面（MDI）以表單為基礎的應用程式，應用程式將能夠支援相同表單的多個實例。

如果您建立具有多個最上層檔支援的應用程式，則桌面是檔的隱含父系，而檔的框架不限於應用程式的工作區。 您可以開啟檔的多個實例，每個實例都有自己的框架、功能表和工作列圖示。 您可以個別關閉**檔**的後續實例，但如果您從初始**實例的 [** 檔案] 功能表中選取 [結束] 選項，應用程式就會關閉所有實例。

SDI、MDI 和多個最上層檔應用程式都是以表單為基礎，並使用檔/視圖架構。

任何以對話方塊為基礎的應用程式（根據定義）都是以表單為基礎。 以對話為基礎的應用程式不使用檔/視圖架構，因此您必須為自己的其他表單管理建立和存取方法。

以表單為基礎的應用程式的基類是[CFormView](cformview-class.md)。 如果您的應用程式具有資料庫支援，則您也可以選取任何衍生自`CFormView`的類別。 表單是任何衍生`CFormView`自的任何視窗，或是從`CFormView`繼承自的任何類別。

即使您使用如[CView](cview-class.md)的基類，您稍後可以藉由新增衍生自`CFormView`的[MFC 類別](adding-an-mfc-class.md)，讓您的應用程式以表單為基礎。

完成 wizard 之後，您的專案就會開啟，而且如果您選取`CFormView` （或繼承自`CFormView`的類別）做為基類，或如果您已建立以對話方塊為基礎的應用程式C++ ，視覺效果就會開啟對話方塊編輯器。 此時，您已準備好設計您的第一個表單。

### <a name="to-begin-creating-a-forms-based-mfc-executable"></a>開始建立以表單為基礎的 MFC 可執行檔

1. 請遵循建立以表單為基礎的 MFC 應用程式的[Mfc 應用程式](creating-an-mfc-application.md)中的指示。

1. 在 [MFC 應用程式精靈] 的 [[應用程式類型](application-type-mfc-application-wizard.md)] 頁面上，選取 [**檔/視圖架構支援**] 核取方塊。

1. 選取 [**單一檔**]、[**多個檔**] 或**多個最上層檔**。

    > [!NOTE]
    >  如果您選擇 SDI、MDI 或多個最上層檔介面應用程式，預設會在 wizard `CView`的 [[產生的類別](generated-classes-mfc-application-wizard.md)] 頁面中，將設定為應用程式視圖的基類。 若要建立以表單為基礎的應用程式`CFormView` ，您必須選取做為應用程式視圖的基類。 請注意，此 wizard 不會針對以表單為基礎的應用程式提供列印支援。

1. 在嚮導的其他頁面上，設定您想要的任何其他專案選項。

1. 按一下 **[完成]** 以產生基本架構應用程式。

如需詳細資訊，請參閱：

- [衍生視圖類別](../derived-view-classes-available-in-mfc.md)

- [檔/視圖架構的替代方案](../alternatives-to-the-document-view-architecture.md)

- [應用程式設計選擇](../application-design-choices.md)

## <a name="see-also"></a>另請參閱

[MFC 應用程式精靈](mfc-application-wizard.md)<br/>
[表單檢視](../form-views-mfc.md)<br/>
[建立檔案總管樣式的 MFC 應用程式](creating-a-file-explorer-style-mfc-application.md)<br/>
[建立網頁瀏覽器樣式的 MFC 應用程式](creating-a-web-browser-style-mfc-application.md)

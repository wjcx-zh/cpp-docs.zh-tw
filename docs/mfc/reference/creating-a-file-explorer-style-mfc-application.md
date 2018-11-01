---
title: 建立檔案總管樣式的 MFC 應用程式
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfcexplorer.project
helpviewer_keywords:
- browsers [MFC], Explorer-style applications
- MFC applications [MFC], Windows Explorer-style
- Explorer-style applications [MFC], creating
ms.assetid: f843ab5d-2d5d-41ca-88a4-badc0d2f8052
ms.openlocfilehash: 3ddeb2e875ccdb45dd0bc2b29a2da3c1498138ab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50564758"
---
# <a name="creating-a-file-explorer-style-mfc-application"></a>建立檔案總管樣式的 MFC 應用程式

許多 Windows 系統應用程式會使用檔案總管 中的使用者介面 (UI)。 當您啟動檔案總管 中時，例如，您會看到用戶端區域線的垂直分割的應用程式。 用戶端區域的左下的方提供瀏覽和瀏覽功能，以及用戶端區域右側會顯示詳細資料選取範圍相關的左窗格中。 當使用者按一下左窗格中的項目時，應用程式重新填入右邊的窗格。 在 MDI 應用程式，您可以使用命令上**檢視**功能表變更顯示在右窗格的詳細資料量。 （在 SDI 或多個最上層的文件的應用程式中，您可以變更使用工具列按鈕的詳細資料）。

窗格的內容取決於應用程式。 在檔案系統瀏覽器中，左的窗格會顯示目錄、 電腦或電腦群組的階層式檢視，而右窗格會顯示資料夾、 個別的檔案，或機器和其相關詳細資料。 內容不一定要的檔案。 它們可能是電子郵件訊息、 錯誤報表或在資料庫中的其他項目。

精靈會為您建立下列類別：

- `CLeftView`類別會定義工作區的左的窗格。 它一律衍生自[CTreeView](../../mfc/reference/ctreeview-class.md)。

- C*ProjName*檢視類別會定義右窗格的 工作區。 根據預設，它衍生自[CListView](../../mfc/reference/clistview-class.md)可以是另一種檢視，根據您指定的類別，但**基底類別**清單中[產生的類別](../../mfc/reference/generated-classes-mfc-application-wizard.md)頁面精靈。

產生的應用程式可以有單一文件介面 (SDI)、 多重文件介面 (MDI) 或使用多個最上層的文件架構。 應用程式會建立每個框架視窗會以垂直方式分割資料集[CSplitterWnd](../../mfc/reference/csplitterwnd-class.md)。 此應用程式類型撰寫程式碼是類似於一般的 MFC 應用程式使用分隔器，撰寫程式碼，不同之處在於這類應用程式具有每個分隔窗格內的個別控制項檢視。

如果您使用的預設清單檢視，在右窗格中，精靈會建立額外的功能表選項 （在 MDI 應用程式） 和工具列按鈕來切換檢視的樣式為大圖示、 小圖示、 清單和詳細資料模式。

### <a name="to-begin-creating-a-file-explorer-style-mfc-executable"></a>若要開始建立檔案總管樣式的 MFC 可執行檔

1. 請遵照[建立 MFC 應用程式](../../mfc/reference/creating-an-mfc-application.md)。

1. 在 MFC 應用程式精靈[應用程式類型](../../mfc/reference/application-type-mfc-application-wizard.md)頁面上，選取**檔案總管**專案樣式。

1. 在精靈的其他頁面上設定您想要的其他任何選項。

1. 按一下 **完成**產生基本架構的應用程式。

如需詳細資訊，請參閱:

- [多重文件類型、檢視和框架視窗](../../mfc/multiple-document-types-views-and-frame-windows.md)

- [衍生的檢視類別](../../mfc/derived-view-classes-available-in-mfc.md)

- [應用程式設計選擇](../../mfc/application-design-choices.md)

## <a name="see-also"></a>另請參閱

[MFC 應用程式精靈](../../mfc/reference/mfc-application-wizard.md)<br/>
[建立網頁瀏覽器樣式的 MFC 應用程式](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)<br/>
[建立表單架構的 MFC 應用程式](../../mfc/reference/creating-a-forms-based-mfc-application.md)


---
title: 建立檔案總管樣式的 MFC 應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfcexplorer.project
dev_langs:
- C++
helpviewer_keywords:
- browsers [MFC], Explorer-style applications
- MFC applications [MFC], Windows Explorer-style
- Explorer-style applications [MFC], creating
ms.assetid: f843ab5d-2d5d-41ca-88a4-badc0d2f8052
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a5b0f5d4bdabc987d4f4177f616ce756c351b8b5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370151"
---
# <a name="creating-a-file-explorer-style-mfc-application"></a>建立檔案總管樣式的 MFC 應用程式
許多 Windows 系統應用程式會使用檔案總管 中的使用者介面 (UI)。 當您啟動檔案總管 中時，例如，您會看到的分割線的用戶端區域的垂直分割的應用程式。 工作區的左半部提供巡覽和瀏覽功能，以及用戶端區域的右側會顯示詳細資料與選取項目相關的左窗格中。 當使用者按一下左窗格中的項目時，應用程式會重新填入右窗格。 MDI 應用程式中，您可以使用命令上**檢視**功能表變更顯示在右窗格中的詳細資料量。 （SDI 或多個最上層文件應用程式中，您可以變更的詳細資料，使用工具列按鈕）。  
  
 窗格的內容取決於應用程式。 在檔案系統的瀏覽器，左的窗格會顯示目錄、 電腦或電腦群組的階層式檢視，而右窗格則顯示資料夾、 個別檔案，或機器和其相關詳細資料。 內容一定沒有的檔案。 它們可能是電子郵件訊息、 錯誤報表或在資料庫中的其他項目。  
  
 精靈會為您建立下列類別：  
  
-   **CLeftView**類別會定義工作區的左的窗格。 它一律衍生自[CTreeView](../../mfc/reference/ctreeview-class.md)。  
  
-   C*ProjName*檢視類別定義的工作區的右窗格。 根據預設，它衍生自[CListView](../../mfc/reference/clistview-class.md)但可以是另一種檢視，請從您指定的類別而**基底類別**清單中[產生的類別](../../mfc/reference/generated-classes-mfc-application-wizard.md)頁面精靈。  
  
 產生的應用程式可以有單一文件介面 (SDI)、 多重文件介面 (MDI)，或者多個最上層文件架構。 每個應用程式建立的框架視窗會垂直分割使用[CSplitterWnd](../../mfc/reference/csplitterwnd-class.md)。 此應用程式類型撰寫程式碼很類似編碼標準的 MFC 應用程式使用分隔器，不同之處在於這類應用程式具有每個分隔窗格內的個別的控制項檢視。  
  
 如果您使用的預設清單檢視在右窗格中，精靈會建立額外的功能表選項 （在 MDI 應用程式只） 和工具列按鈕來切換檢視的樣式為大圖示、 小圖示、 清單和詳細資料模式。  
  
### <a name="to-begin-creating-a-file-explorer-style-mfc-executable"></a>若要開始建立檔案總管樣式的 MFC 可執行檔  
  
1.  請遵照[建立 MFC 應用程式](../../mfc/reference/creating-an-mfc-application.md)。  
  
2.  在 MFC 應用程式精靈[應用程式類型](../../mfc/reference/application-type-mfc-application-wizard.md)頁面上，選取**檔案總管**專案樣式。  
  
3.  其他的精靈頁面上設定您想要的任何其他選項。  
  
4.  按一下**完成**產生基本架構應用程式。  
  
 如需詳細資訊，請參閱:  
  
-   [多重文件類型、檢視和框架視窗](../../mfc/multiple-document-types-views-and-frame-windows.md)  
  
-   [衍生的檢視類別](../../mfc/derived-view-classes-available-in-mfc.md)  
  
-   [應用程式設計選擇](../../mfc/application-design-choices.md)  
  
## <a name="see-also"></a>另請參閱  
 [MFC 應用程式精靈](../../mfc/reference/mfc-application-wizard.md)   
 [建立 Web 瀏覽器樣式的 MFC 應用程式](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)   
 [建立表單架構的 MFC 應用程式](../../mfc/reference/creating-a-forms-based-mfc-application.md)


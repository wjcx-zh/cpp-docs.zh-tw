---
title: 將表單插入專案中
ms.date: 11/04/2016
helpviewer_keywords:
- inserting forms [MFC]
- Insert New dialog box [MFC]
- forms, adding to projects
ms.assetid: f3bd2998-3ce2-496d-ac5c-57ca70eec7cb
ms.openlocfilehash: 8e3162ac3917781920130bcbed23864eb90afa59
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618423"
---
# <a name="inserting-a-form-into-a-project"></a>將表單插入專案中

表單提供方便的控制項容器。 只要應用程式支援 MFC 程式庫，您就可以輕鬆地在應用程式中插入以 MFC 為基礎的表單。

### <a name="to-insert-a-form-into-your-project"></a>將表單插入專案中

1. 從 [類別檢視] 中，選取您要加入表單的專案，然後按一下滑鼠右鍵。

1. 從快捷方式功能表按一下 [**新增**]，然後按一下 [**新增類別**]。

   如果無法使用 [**新增表單**] 命令，您的專案可能會以 ACTIVE TEMPLATE LIBRARY （ATL）為基礎。 若要在 ATL 專案中加入表單，您必須在第一次建立專案時[指定特定的設定](../atl/reference/application-settings-atl-project-wizard.md)。

1. 從 [ **mfc** ] 資料夾，按一下 [ **mfc 類別**]。

1. 使用 MFC 類別 Wizard，讓新的類別衍生自[CFormView](reference/cformview-class.md)。

Visual C++ 會將表單新增至您的應用程式，在對話方塊編輯器中開啟它，以便開始加入控制項並處理其整體設計。

您可能想要執行下列額外步驟（不適用於以對話為基礎的應用程式）：

1. 覆寫 `OnUpdate` 成員函式。

1. 執行成員函式，將資料從您的視圖移至您的檔。

1. 建立成員函式 `OnPrint` 。

## <a name="see-also"></a>另請參閱

[表單檢視](form-views-mfc.md)

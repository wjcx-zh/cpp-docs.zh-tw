---
title: 建立 MFC ActiveX 控制項
ms.date: 08/19/2019
f1_keywords:
- vc.appwiz.activex.project
helpviewer_keywords:
- MFC ActiveX controls [MFC], creating
- ActiveX controls [MFC], creating
ms.assetid: 8bd5a93c-d04d-414e-bb28-163fdc1c0dd5
ms.openlocfilehash: 5e0a81d6a01632bcfadccd241f3a485e6d332627
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077451"
---
# <a name="creating-an-mfc-activex-control"></a>建立 MFC ActiveX 控制項

ActiveX 控制項程式是一種模組化程式，設計用來為父應用程式提供特定類型的功能。 例如，您可以建立控制項，例如在對話方塊中使用的按鈕，或用來在網頁中使用的工具列。

>[!IMPORTANT]
> ActiveX 是不應該用於新開發的舊版技術。 如需詳細資訊，請參閱[ActiveX 控制項](../activex-controls.md)。

建立 MFC ActiveX 控制項最簡單的方式，是使用[MFC Activex 控制項 Wizard](../../mfc/reference/mfc-activex-control-wizard.md)。

### <a name="to-create-an-mfc-activex-control-using-the-mfc-activex-control-wizard"></a>使用 MFC ActiveX 控制項 Wizard 建立 MFC ActiveX 控制項

1. 遵循[建立 MFC 應用程式](creating-an-mfc-application.md)說明主題中的指示，但從可用範本的清單中選擇 [ **MFC ActiveX 控制項**]。

1. 使用 MFC ActiveX 控制項 Wizard 來定義您的[應用程式設定](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)、[控制項名稱](../../mfc/reference/control-names-mfc-activex-control-wizard.md)和[控制設定](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)。

    > [!NOTE]
    >  若要保留精靈的預設值，請略過此步驟。

1. 按一下 [完成] 以關閉精靈，並在開發環境中開啟新專案。

建立專案之後，您可以查看**方案總管**中建立的檔案。 如需精靈建立之專案檔案的詳細資訊，請參閱專案所產生的 ReadMe.txt 檔案。 如需檔案類型的詳細資訊，請參閱[為 Visual Studio C++ 專案建立的檔案類型](../../build/reference/file-types-created-for-visual-cpp-projects.md)。

建立專案之後，您可以使用程式碼嚮導[來新增函](../../ide/add-member-function-wizard.md)式、[變數](../../ide/add-member-variable-wizard.md)、[事件](../../ide/add-event-wizard.md)、[屬性](../../ide/names-add-property-wizard.md)和[方法](../../ide/add-method-wizard.md)。 如需自訂 ActiveX 控制項的詳細資訊，請參閱[MFC Activex 控制項](../../mfc/mfc-activex-controls.md)。

## <a name="see-also"></a>另請參閱

[使用程式碼精靈新增功能](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[屬性頁](../../build/reference/property-pages-visual-cpp.md)

---
title: 建立 MFC ActiveX 控制項
ms.date: 08/19/2019
f1_keywords:
- vc.appwiz.activex.project
helpviewer_keywords:
- MFC ActiveX controls [MFC], creating
- ActiveX controls [MFC], creating
ms.assetid: 8bd5a93c-d04d-414e-bb28-163fdc1c0dd5
ms.openlocfilehash: 19e9ca6f985423bb01a8dea38988c5dcf7285683
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91505968"
---
# <a name="creating-an-mfc-activex-control"></a>建立 MFC ActiveX 控制項

ActiveX 控制項程式是設計用來為父應用程式提供特定類型功能的模組化程式。 例如，您可以建立一個控制項，例如在對話方塊中使用的按鈕，或是用來在網頁中使用的工具列。

>[!IMPORTANT]
> ActiveX 是不應該用於新開發的舊版技術。 如需詳細資訊，請參閱 [ActiveX 控制項](../activex-controls.md)。

建立 MFC ActiveX 控制項最簡單的方式，就是使用 [Mfc Activex 控制項 Wizard](../../mfc/reference/mfc-activex-control-wizard.md)。

### <a name="to-create-an-mfc-activex-control-using-the-mfc-activex-control-wizard"></a>使用 MFC ActiveX 控制項 Wizard 建立 MFC ActiveX 控制項

1. 遵循 [說明] 主題中的指示來 [建立 Mfc 應用程式](creating-an-mfc-application.md) ，但從可用範本的清單中選擇 [ **MFC ActiveX 控制項** ]。

1. 使用 MFC ActiveX Control Wizard 定義您的 [應用程式設定](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)、 [控制項名稱](../../mfc/reference/control-names-mfc-activex-control-wizard.md)和 [控制設定](../../mfc/reference/control-settings-mfc-activex-control-wizard.md) 。

    > [!NOTE]
    >  若要保留精靈的預設值，請略過此步驟。

1. 按一下 [完成]**** 以關閉精靈，並在開發環境中開啟新專案。

建立專案之後，您可以查看 **方案總管**中建立的檔案。 如需精靈建立之專案檔案的詳細資訊，請參閱專案所產生的 ReadMe.txt 檔案。 如需檔案類型的詳細資訊，請參閱[為 Visual Studio C++ 專案建立的檔案類型](../../build/reference/file-types-created-for-visual-cpp-projects.md)。

建立專案 [之後，您](../../ide/adding-a-member-function-visual-cpp.md#add-member-function-wizard)可以使用程式碼嚮導來新增函式、 [變數](../../ide/adding-a-member-variable-visual-cpp.md#add-member-variable-wizard)、 [事件](../../ide/adding-an-event-visual-cpp.md#add-event-wizard)、 [屬性](../../ide/adding-a-property-visual-cpp.md#names-add-property-wizard)和 [方法](../../ide/adding-a-method-visual-cpp.md#add-method-wizard)。 如需自訂 ActiveX 控制項的詳細資訊，請參閱 [MFC Activex 控制項](../../mfc/mfc-activex-controls.md)。

## <a name="see-also"></a>另請參閱

[使用程式碼精靈新增功能](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[屬性頁](../../build/reference/property-pages-visual-cpp.md)

---
title: MFC ActiveX 控制項精靈
ms.date: 09/12/2018
f1_keywords:
- vc.appwiz.mfc.ctl.overview
helpviewer_keywords:
- ActiveX controls [MFC], MFC
- MFC ActiveX controls [MFC], wizards
- OLE controls [MFC], creating
- MFC ActiveX Control Wizard
- OLE controls [MFC]
ms.assetid: f19d698c-bdc3-4c74-af97-3d6ccb441b75
ms.openlocfilehash: cec4c3aa6aedfa7a1f8234c6cc2355970d453f56
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412761"
---
# <a name="mfc-activex-control-wizard"></a>MFC ActiveX 控制項精靈

ActiveX 控制項是特定型別的[automation 伺服程式](../../mfc/automation-servers.md); 它是可重複使用的元件。 裝載 ActiveX 控制項的應用程式[自動化用戶端](../../mfc/automation-clients.md)該控制項。 如果您的目標是要建立這類可重複使用的元件，然後使用這個精靈來建立您的控制項。 請參閱[MFC ActiveX 控制項](../../mfc/mfc-activex-controls.md)如需詳細資訊。

>[!IMPORTANT]
> ActiveX 是舊版的技術，不應用於新的開發。 如需有關取代 ActiveX 的現代技術的詳細資訊，請參閱[ActiveX 控制項](../activex-controls.md)。

或者，您可以在其中建立 automation 伺服器 MFC 應用程式使用[MFC 應用程式精靈](../../mfc/reference/mfc-application-wizard.md)。

使用此精靈建立 ActiveX 控制項可以具有使用者介面，或可以是不可見。 您可以指定此選項[控制設定](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)精靈中的頁面。 計時器控制項是 ActiveX 控制項，您會想要隱藏的範例。

ActiveX 控制項可以有複雜的使用者介面。 有些控制項可能就像封裝的表單： 單一控制項包含許多欄位，每個 Windows 控制項本身。 比方說，實作成 MFC ActiveX 控制項的自動部分物件可能會呈現類似格式的使用者介面，讓使用者可讀取，並編輯組件編號、 組件名稱和其他資訊。 請參閱[MFC ActiveX 控制項](../../mfc/mfc-activex-controls.md)如需詳細資訊。

如果您要建立 ActiveX 物件的容器，請參閱[建立 ActiveX 控制項容器](../../mfc/reference/creating-an-mfc-activex-control-container.md)。

MFC 入門版計畫包含C++原始檔 (.cpp) 檔案、 資源 (.rc) 檔，以及專案 (.vcxproj) 檔案。 這些入門檔案中產生的程式碼是以 MFC 為基礎。

下面範例會顯示工作和 ActiveX 控制項的增強功能的類型：

- [最佳化 ActiveX 控制項](../../mfc/mfc-activex-controls-optimization.md)

- [將內建事件加入至 ActiveX 控制項](../../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md)

- [加入自訂事件](../../mfc/mfc-activex-controls-adding-custom-events.md)

- [加入內建方法](../../mfc/mfc-activex-controls-adding-stock-methods.md)

- [新增自訂方法](../../mfc/mfc-activex-controls-adding-custom-methods.md)

- [加入內建屬性](../../mfc/mfc-activex-controls-adding-stock-properties.md)

- [加入自訂屬性](../../mfc/mfc-activex-controls-adding-custom-properties.md)

- [在 ActiveX 控制項容器中程式設計 ActiveX 控制項](../../mfc/programming-activex-controls-in-a-activex-control-container.md)

## <a name="overview"></a>總覽

此精靈頁面說明目前的應用程式設定，您要建立 MFC ActiveX 控制項專案。 依預設，此精靈建立專案，如下所示：

- 預設專案會產生任何執行階段授權或說明檔案。 您可以變更這些預設設定，在[應用程式設定](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)頁面。 只將 ActiveX 控制項精靈的此頁面所進行的選擇會反映在**概觀**頁面。

- 專案會包含在控制項類別和屬性頁類別，根據專案的名稱。 您可以編輯您的專案和檔案名稱的名稱上[控制項名稱](../../mfc/reference/control-names-mfc-activex-control-wizard.md)頁面。

- 控制項沒有現有的 Windows 控制項為基礎，啟動時將它變成可見，具有使用者介面，並包含**關於** 對話方塊。 您可以變更這些預設設定，在[控制設定](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)頁面。

## <a name="see-also"></a>另請參閱

[建立和管理 Visual C++ 專案](../../build/creating-and-managing-visual-cpp-projects.md)<br/>
[Visual C++ 專案類型](../../build/reference/visual-cpp-project-types.md)<br/>
[概念](../../atl/active-template-library-atl-concepts.md)

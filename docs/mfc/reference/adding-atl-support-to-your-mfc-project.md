---
title: 將 ATL 支援加入至 MFC 專案
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.adding.atl.mfc
helpviewer_keywords:
- MFC, ATL support
- ATL, MFC projects
ms.assetid: b5fe15d6-7752-4818-b9f9-62482ad35c95
ms.openlocfilehash: fba79db013cd9f4cc62ba5826b53e5fa9b15c83a
ms.sourcegitcommit: bf1940a39029dbbd861f95480f55e5e8bd25cda0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70108407"
---
# <a name="adding-atl-support-to-your-mfc-project"></a>將 ATL 支援加入至 MFC 專案

如果您已經建立以 MFC 為基礎的應用程式, 則可以使用 IDE 輕鬆地加入 Active Template Library (ATL) 的支援。

> [!NOTE]
>  這項支援只適用於新增至 MFC 可執行檔或 DLL 專案的簡單 COM 物件。 您可以將其他 COM 物件 (包括 ActiveX 控制項) 新增至 MFC 專案, 但這些物件可能無法如預期般運作。

::: moniker range=">=vs-2019"

1. 在方案總管中, 以滑鼠右鍵按一下專案節點。

1. 在捷徑功能表上，按一下 [新增]，然後按一下 [新增項目]。

1. 選擇左窗格中的 [ **atl** ], 然後選擇中間窗格中的 [ **atl 支援**]。

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-add-atl-support-to-your-mfc-project"></a>將 ATL 支援新增至 MFC 專案

1. 在方案總管中, 以滑鼠右鍵按一下專案節點。

1. 在捷徑功能表上，按一下 [加入]，然後按一下 [加入類別]。

1. 在左窗格中選取 [ **atl** ], 然後選擇中央窗格中的 [**將 atl 支援新增至 MFC 專案**]。

::: moniker-end

如需新增 ATL 支援如何變更您的 MFC 專案程式碼的詳細資訊, 請參閱[Atl Wizard 新增的 Atl 支援詳細資料](../../mfc/reference/details-of-atl-support-added-by-the-atl-wizard.md)

## <a name="see-also"></a>另請參閱

[新增類別](../../ide/adding-a-class-visual-cpp.md)<br/>
[使用程式碼精靈新增功能](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[新增成員函式](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[新增成員變數](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[覆寫虛擬函式](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[MFC 訊息處理常式](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[巡覽類別結構](../../ide/navigate-code-cpp.md)

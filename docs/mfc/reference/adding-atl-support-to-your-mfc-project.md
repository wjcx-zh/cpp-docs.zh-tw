---
title: 將 ATL 支援加入至 MFC 專案
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.adding.atl.mfc
helpviewer_keywords:
- MFC, ATL support
- ATL, MFC projects
ms.assetid: b5fe15d6-7752-4818-b9f9-62482ad35c95
ms.openlocfilehash: 05c4e8ba54d9a573b422f136c9e8cf69e48d1c9a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371675"
---
# <a name="adding-atl-support-to-your-mfc-project"></a>將 ATL 支援加入至 MFC 專案

如果您已經創建了基於 MFC 的應用程式,則可以使用 IDE 輕鬆添加對活動範本庫 (ATL) 的支援。

> [!NOTE]
> 這項支援只適用於新增至 MFC 可執行檔或 DLL 專案的簡單 COM 物件。 您可以將其他 COM 物件(包括 ActiveX 控制項)添加到 MFC 專案中,但物件可能無法按預期方式運行。

::: moniker range=">=vs-2019"

1. 在解決方案資源管理器中,右鍵單擊專案節點。

1. 在捷徑功能表上，按一下 [新增]****，然後按一下 [新增項目]****。

1. 在左邊窗格中選擇**ATL,** 然後在中心窗格中選擇**ATL 支援**。

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-add-atl-support-to-your-mfc-project"></a>將 ATL 支援新增到 MFC 專案

1. 在解決方案資源管理器中,右鍵單擊專案節點。

1. 在捷徑功能表上，按一下 [加入]****，然後按一下 [加入類別]****。

1. 在左邊窗格中選擇**ATL,** 然後在中心窗格中選擇 **「將 ATL 支援添加到 MFC 專案**」。

::: moniker-end

有關新增 ATL 支援如何變更 MFC 專案代碼的詳細資訊,請參閱[ATL 精靈新增的 ATL 支援的詳細資訊](../../mfc/reference/details-of-atl-support-added-by-the-atl-wizard.md)

## <a name="see-also"></a>另請參閱

[新增類別](../../ide/adding-a-class-visual-cpp.md)<br/>
[使用程式碼精靈新增功能](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[新增成員函式](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[新增成員變數](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[覆寫虛擬函式](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[MFC 訊息處理常式](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[巡覽類別結構](../../ide/navigate-code-cpp.md)

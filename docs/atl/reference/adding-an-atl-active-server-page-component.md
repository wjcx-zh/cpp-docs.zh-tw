---
title: 新增 ATL Active Server Page 元件
ms.date: 05/09/2019
ms.assetid: 7be2204c-6e58-4099-8892-001b848c8987
ms.openlocfilehash: b6c1d23efdff6885cc8ab900aaf552db39631e6e
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65706922"
---
# <a name="adding-an-atl-active-server-page-component"></a>新增 ATL Active Server Page 元件


::: moniker range="vs-2019"

Visual Studio 2019 及更新版本中未提供 ATL Active Server Page 元件精靈。

::: moniker-end

::: moniker range="<=vs-2017"

若要將 Active Template Library (ATL) 物件新增至您的專案中，您的專案必須已經建立為 ATL COM 應用程式，或含有 ATL 支援的 MFC 應用程式。 您可以使用 [ATL 專案精靈](../../atl/reference/atl-project-wizard.md) 建立 ATL 應用程式；您可以從 [加入類別對話方塊](../../ide/add-class-dialog-box.md) 對話方塊選取 [將 ATL 支援加入 MFC]；或者您可以[將 ALT 物件新增至 MFC 應用程式](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)，來實作 MFC 應用程式的 ATL 支援。

Active Server Page 元件是 Internet Information Services 架構的一部分，可提供下列進階的 Web 程式開發功能：

- 您可以將 ASP 元件內嵌到您的 HTML 頁面，以建立動態且與瀏覽器無關的內容。

- 您可以使用 ASP 網頁提供標準式的資料庫連線。

- 您可以為您的 Web 應用程式使用 ASP 錯誤處理功能。

## <a name="to-add-an-atl-active-server-pages-component-to-your-project"></a>若要將 ATL Active Server Page 元件新增至您的專案

1. 在 [方案總管] 中，以滑鼠右鍵按一下您要在其中新增 ATL Active Server Page 元件之專案的名稱。

1. 從捷徑功能表按一下 [新增]，然後按一下 [新增類別]。

1. 在 [加入類別](../../ide/add-class-dialog-box.md) 對話方塊的 [範本] 窗格中，按一下 [ATL Active Server Page 元件]，然後按一下 [開啟] 以顯示 [ATL Active Server Page 元件精靈](../../atl/reference/atl-active-server-page-component-wizard.md)。

::: moniker-end

## <a name="see-also"></a>另請參閱

[新增類別](../../ide/adding-a-class-visual-cpp.md)<br/>
[在 ATL 專案中新增介面](../../atl/reference/adding-a-new-interface-in-an-atl-project.md)<br/>
[將連接點新增至物件](../../atl/adding-connection-points-to-an-object.md)<br/>
[新增方法](../../ide/adding-a-method-visual-cpp.md)<br/>
[MFC 類別](../../mfc/reference/adding-an-mfc-class.md)<br/>
[新增泛型 C++ 類別](../../ide/adding-a-generic-cpp-class.md)

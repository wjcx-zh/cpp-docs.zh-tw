---
title: 新增 ATL OLE DB 提供者
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB, adding ATL OLE DB provider to projects
- ATL projects, adding ATL OLE DB providers
- ATL OLE DB providers
ms.assetid: 26fba1e3-880f-4bc6-90e5-2096a48a3a6c
ms.openlocfilehash: 36c07da6249a106836433e127f95258d4ed5b509
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65706936"
---
# <a name="adding-an-atl-ole-db-provider"></a>新增 ATL OLE DB 提供者

::: moniker range="vs-2019"

Visual Studio 2019 及更新版本中未提供 ATL OLE DB 提供者精靈。

::: moniker-end

::: moniker range="<=vs-2017"

使用此精靈，將 ATL OLE DB 提供者新增至專案。 ATL OLE DB 提供者會由資料來源、工作階段、命令及資料列集類別所組成。 專案必須已建立為 ATL COM 應用程式。

## <a name="to-add-an-atl-ole-db-provider-to-your-project"></a>將 ATL OLE DB 提供者新增至專案

1. 在 [類別檢視] 中，以滑鼠右鍵按一下專案。 在捷徑功能表上，按一下 [新增]，然後按一下 [新增類別]。

1. 在 [Visual C++ ] 資料夾中，按兩下 [ATL OLE DB 提供者] 圖示或加以選取，然後按一下 [開啟]。

   ATL OLE DB 提供者精靈隨即開啟。

1. 定義設定，如 [ATL OLE DB 提供者精靈](../../atl/reference/atl-ole-db-provider-wizard.md)中所述。

1. 按一下 [完成] 即可關閉精靈，其將在您的專案中插入新建立的 OLE DB 提供者程式碼。

::: moniker-end

## <a name="see-also"></a>另請參閱

[使用程式碼精靈新增功能](../../ide/adding-functionality-with-code-wizards-cpp.md)

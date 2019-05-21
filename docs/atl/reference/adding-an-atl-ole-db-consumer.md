---
title: 加入 ATL OLE DB 消費者
ms.date: 05/09/2019
helpviewer_keywords:
- ATL OLE DB consumers
ms.assetid: f940a513-4e42-4148-b521-dd0d7dc89fa2
ms.openlocfilehash: 1e384a283a2a149faa5b8d6e0817eac3cacfeff9
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65706911"
---
# <a name="adding-an-atl-ole-db-consumer"></a>加入 ATL OLE DB 消費者

::: moniker range="vs-2019"

Visual Studio 2019 及更新版本中未提供 ATL OLE DB 消費者精靈。 您仍然可以手動加入功能。 如需詳細資訊，請參閱[未使用精靈建立消費者](../../data/oledb/creating-a-consumer-without-using-a-wizard.md)。

::: moniker-end

::: moniker range="<=vs-2017"

使用此精靈，將 ATL OLE DB 消費者加入至專案。 ATL OLE DB 消費者包含一個 OLE DB 存取子類別以及存取資料來源所需的資料繫結。 專案必須已建立為 ATL COM 應用程式，或已建立為包含 ATL 支援的 MFC 或 Win32 應用程式 (這會自動加入 ATL OLE DB 消費者精靈)。

> [!NOTE]
> 您可以將 OLE DB 消費者加入至 MFC 專案。 如果您這樣做，ATL OLE DB 消費者精靈就會將必要的 COM 支援加入至您的專案。 這假設您在建立 MFC 專案時選取了 [ActiveX 控制項] 核取方塊 (位於 MFC 專案應用程式精靈的 [進階功能] 頁面)，預設會核取此核取方塊。 選取此選項可確保應用程式會呼叫 `CoInitialize` 和 `CoUninitialize`。 如果您未在建立 MFC 專案時選取 [ActiveX 控制項]，就必須在主要程式碼中呼叫 `CoInitialize` 和 `CoUninitialize`。

## <a name="to-add-an-atl-ole-db-consumer-to-your-project"></a>將 ATL OLE DB 消費者加入至專案

1. 在 [類別檢視] 中，以滑鼠右鍵按一下專案。 在捷徑功能表上，按一下 [加入]，然後按一下 [加入類別]。

1. 在 [Visual C++] 資料夾中，按兩下 [ATL OLE DB 消費者] 圖示，或者選取它並按一下 [開啟]。

   ATL OLE DB 消費者精靈隨即開啟。

1. 定義設定，如 [ATL OLE DB 消費者精靈](../../atl/reference/atl-ole-db-consumer-wizard.md)中所述。

1. 按一下 [完成] 以關閉精靈。 新建立的 OLE DB 消費者程式碼將會插入至您的專案。

::: moniker-end

## <a name="see-also"></a>另請參閱

[使用程式碼精靈新增功能](../../ide/adding-functionality-with-code-wizards-cpp.md)

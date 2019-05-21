---
title: 建立簡單唯讀提供者
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: ade8ccdd-9ea4-4e46-a964-18460c2a2401
ms.openlocfilehash: c0f31818002ce4611926d942b3bc556e31c1ae6f
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2019
ms.locfileid: "65524716"
---
# <a name="creating-a-simple-read-only-provider"></a>建立簡單唯讀提供者

::: moniker range="vs-2019"

Visual Studio 2019 及更新版本中未提供 ATL OLE DB 提供者精靈。

::: moniker-end

::: moniker range="vs-2017"

當您使用 [ATL 專案精靈] 和 [ATL OLE DB 提供者精靈] 建立 OLE DB 提供者時，您可以加入您想要支援的其他功能。 若要開始設計您的提供者，請檢查您要在哪些情況下傳送給消費者哪些種類的資料。 決定您需要支援命令、交易還是其他選用物件特別重要。 預先進行良好的設計可加速實作和測試。

此範例會以兩個部分呈現：

- 第一個部分顯示如何[建立簡單的唯讀提供者](../../data/oledb/implementing-the-simple-read-only-provider.md)來讀取一組字串。

- 第二個部分顯示如何新增 `IRowsetLocate` 介面來[增強簡單的唯讀提供者](../../data/oledb/enhancing-the-simple-read-only-provider.md)。

::: moniker-end

## <a name="see-also"></a>另請參閱

[建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)<br/>

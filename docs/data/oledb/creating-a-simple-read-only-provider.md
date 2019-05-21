---
title: 建立簡單唯讀提供者
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: ade8ccdd-9ea4-4e46-a964-18460c2a2401
ms.openlocfilehash: 466530cb8c2ebca7f1c87370389309d3a0486e26
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707615"
---
# <a name="creating-a-simple-read-only-provider"></a>建立簡單唯讀提供者

::: moniker range="vs-2019"

Visual Studio 2019 及更新版本中未提供 ATL OLE DB 提供者精靈。

::: moniker-end

::: moniker range="<=vs-2017"

當您使用 [ATL 專案精靈] 和 [ATL OLE DB 提供者精靈] 建立 OLE DB 提供者時，您可以加入您想要支援的其他功能。 若要開始設計您的提供者，請檢查您要在哪些情況下傳送給消費者哪些種類的資料。 決定您需要支援命令、交易還是其他選用物件特別重要。 預先進行良好的設計可加速實作和測試。

此範例會以兩個部分呈現：

- 第一個部分顯示如何[建立簡單的唯讀提供者](../../data/oledb/implementing-the-simple-read-only-provider.md)來讀取一組字串。

- 第二個部分顯示如何新增 `IRowsetLocate` 介面來[增強簡單的唯讀提供者](../../data/oledb/enhancing-the-simple-read-only-provider.md)。

::: moniker-end

## <a name="see-also"></a>另請參閱

[建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)<br/>

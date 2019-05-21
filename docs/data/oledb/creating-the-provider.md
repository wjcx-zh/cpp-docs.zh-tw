---
title: 建立提供者
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB providers, creating
ms.assetid: 2506ba8f-010d-4231-aac1-387432f7b6b9
ms.openlocfilehash: 7a8b4caf85ff7d0310c97cb953739796cca21c43
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707583"
---
# <a name="creating-the-provider"></a>建立提供者

::: moniker range="vs-2019"

Visual Studio 2019 及更新版本中未提供 ATL OLE DB 提供者精靈。

::: moniker-end

::: moniker range="<=vs-2017"

## <a name="to-create-an-ole-db-provider-with-the-atl-ole-db-provider-wizard"></a>使用 ATL OLE DB 提供者精靈建立 OLE DB 提供者

1. 以滑鼠右鍵按一下專案。

1. 在捷徑功能表上，按一下 [加入]，然後按一下 [加入類別]。

1. 在 [加入類別] 對話方塊的 [已安裝]>[Visual C++ ]>[ATL] 下方，選取 [ATL OLEDB 提供者] 圖示，然後按一下 [開啟]。

1. 在 [ATL OLE DB 提供者精靈] 的 [簡短名稱] 方塊中，輸入您提供者的簡短名稱。 下列主題所使用的簡短名稱為 *Custom*，但您可以使用其他名稱。 其他名稱方塊會根據您輸入的名稱來填入。

1. 視需要編輯其他名稱方塊。 除了物件和檔案名稱，您還能編輯下列項目：

   - **Coclass**：COM 用來建立提供者的名稱。

   - **ProgID**：程式設計識別碼，這是可用來取代 GUID 的文字字串。

   - **版本**：與 ProgID 和 Coclass 搭配使用來產生版本相依的程式設計識別碼。

1. 按一下 [ **完成**]。

::: moniker-end

## <a name="see-also"></a>另請參閱

[建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)

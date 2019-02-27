---
title: 預先定義的符號 ID
ms.date: 02/14/2019
helpviewer_keywords:
- symbols [C++], predefined IDs
- predefined symbol IDs
ms.assetid: 91a5d610-1a04-47e8-b8a4-63ad650a90df
ms.openlocfilehash: 7d3581a9f6f2a2080f72634a01d3417ffecf82a4
ms.sourcegitcommit: f127b08f114b8d6cab6b684febcb6f2ae0e055ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2019
ms.locfileid: "56954909"
---
# <a name="predefined-symbol-ids"></a>預先定義的符號 ID

當您開始新的專案時，視專案類型而定，已預先定義一些符號 ID 供您使用。 這些符號 ID 支援各種程式庫和專案類型，例如 MFC。 它們代表通常包含在任何應用程式中的一般工作，或硬體項目 (如滑鼠或印表機) 的動作。

使用資源時，這些符號 ID 變得重要。 編輯快速鍵對應表，其中有些已與虛擬按鍵相關聯時，它們會出現。 它們也可供您透過[屬性 視窗](/visualstudio/ide/reference/properties-window)。 您可以將任何預先定義的符號 Id 指派給新的資源，或您可以將快速鍵指派為 them 與的符號 ID 會自動關聯該按鍵組合相關聯的功能。

這些程式庫有預先定義的符號，將顯示為專案的一部分：

- [ATL 預先定義的符號](../windows/atl-predefined-symbols.md)

- [MFC 預先定義的符號](../windows/mfc-predefined-symbols.md)

- [Win32 預先定義的符號](../windows/win32-predefined-symbols.md)

> [!NOTE]
> 預先定義的符號一律是唯讀的。

## <a name="requirements"></a>需求

Win32、MFC 或 ATL

## <a name="see-also"></a>另請參閱

[資源識別項 (符號)](../windows/symbols-resource-identifiers.md)<br/>
[如何：建立符號](../windows/creating-new-symbols.md)<br/>
[如何：管理符號](../windows/changing-a-symbol-or-symbol-name-id.md)<br/>
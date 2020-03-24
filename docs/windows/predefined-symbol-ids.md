---
title: 預先定義的符號 ID
ms.date: 02/14/2019
helpviewer_keywords:
- symbols [C++], predefined IDs
- predefined symbol IDs
ms.assetid: 91a5d610-1a04-47e8-b8a4-63ad650a90df
ms.openlocfilehash: 8f7fcba864f4e1a47d217d684b87c257503aeb13
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215159"
---
# <a name="predefined-symbol-ids"></a>預先定義的符號 ID

當您開始新的專案時，視專案類型而定，已預先定義一些符號 ID 供您使用。 這些符號 ID 支援各種程式庫和專案類型，例如 MFC。 它們代表通常包含在任何應用程式中的一般工作，或硬體項目 (如滑鼠或印表機) 的動作。

使用資源時，這些符號 ID 變得重要。 當您編輯快速鍵對應表，而且其中一些已與虛擬機器碼相關聯時，即可使用它們。 您也可以透過[屬性視窗](/visualstudio/ide/reference/properties-window)取得這些功能。 您可以將任何預先定義的符號 Id 指派給新的資源，也可以將快速鍵指派給它們，而與符號識別碼相關聯的功能會自動與該按鍵組合產生關聯。

程式庫具有預先定義的符號，將會顯示為專案的一部分：

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

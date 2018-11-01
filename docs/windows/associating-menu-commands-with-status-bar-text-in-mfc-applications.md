---
title: 將功能表命令和 MFC 應用程式內的狀態列文字建立關聯
ms.date: 11/04/2016
helpviewer_keywords:
- status bars [C++], associating menu items
- menus [C++], status bar text
ms.assetid: 757c0e02-bc97-493f-bccd-6cc6887ebc64
ms.openlocfilehash: fc39695358a9c1f2f62878487a5e4fedf5db2b82
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468883"
---
# <a name="associating-menu-commands-with-status-bar-text-in-mfc-applications"></a>將功能表命令和 MFC 應用程式內的狀態列文字建立關聯

MFC 應用程式可以針對每個使用者可以選取功能表命令顯示描述性文字。 您可以將文字字串指派給每個功能表命令使用**提示**中的屬性**屬性**視窗。 如果您在 [字串表](../windows/string-editor.md) 中具有其識別碼與命令相同的字串，則當使用者將滑鼠停留在功能表項目時，MFC 應用程式將在執行中應用程式的狀態列中自動顯示此字串資源。

### <a name="to-associate-a-menu-command-with-a-status-bar-text-string"></a>若要建立功能表命令與狀態列文字字串的關聯

1. 在 [ **功能表** ] 編輯器中，選取功能表命令。

2. 在 [屬性視窗](/visualstudio/ide/reference/properties-window)的 [ **提示** ] 方塊中，輸入相關聯的狀態列文字。

## <a name="requirements"></a>需求

MFC

## <a name="see-also"></a>另請參閱

[字串 (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[將命令新增至功能表](../windows/adding-commands-to-a-menu.md)<br/>
[功能表編輯器](../windows/menu-editor.md)
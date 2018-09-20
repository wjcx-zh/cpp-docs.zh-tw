---
title: 如何： 更新使用者介面物件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- menus [MFC], updating as context changes
- user interface objects [MFC], updating
- user interface objects [MFC]
- update handlers [MFC]
- enabling UI elements [MFC]
- disabling menus [MFC]
- updating user-interface objects [MFC]
- disabling UI elements [MFC]
- commands [MFC], updating UI
- enabling menus [MFC]
ms.assetid: 82f09773-c978-427b-b321-05a6143b7369
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8afe8f6f7594c2dff75125aa56a210505bf5301d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410581"
---
# <a name="how-to-update-user-interface-objects"></a>如何：更新使用者介面物件

通常，功能表項目和工具列按鈕有一種以上的狀態。 例如，目前內容未提供的功能表項目會變成灰色 (表示停用)。 功能表項目也可以是已核取或未核取。 工具列按鈕若無法使用也可以關閉，也可以是已核取。

誰負責更新這些項目，因為如果功能表項目產生命令時，由邏輯上來說，程式狀況變更 （例如） 文件的狀態，合理文件更新功能表項目。 文件可能包含更新所依據的資訊。

如果命令具有多重使用者介面物件 (可能是功能表項目和工具列按鈕)，則兩者都會路由至相同處理函式。 這會在單一位置封裝所有用於相等使用者介面物件的使用者介面更新程式碼。

這個架構會提供用於自動更新使用者介面物件的方便介面。 您可以選擇以其他方法進行更新，不過所提供的介面是有效率且容易使用的。

下列主題說明更新處理常式的使用：

- [呼叫更新處理常式的時機](../mfc/when-update-handlers-are-called.md)

- [ON_UPDATE_COMMAND_UI 巨集](../mfc/on-update-command-ui-macro.md)

- [CCmdUI 類別](../mfc/the-ccmdui-class.md)

## <a name="see-also"></a>另請參閱

[功能表](../mfc/menus-mfc.md)


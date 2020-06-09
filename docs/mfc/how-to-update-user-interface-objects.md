---
title: 如何：更新使用者介面物件
ms.date: 11/04/2016
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
ms.openlocfilehash: aec4067a7b5854ef872cfcef19a15db8438dd795
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626393"
---
# <a name="how-to-update-user-interface-objects"></a>如何：更新使用者介面物件

通常，功能表項目和工具列按鈕有一種以上的狀態。 例如，目前內容未提供的功能表項目會變成灰色 (表示停用)。 功能表項目也可以是已核取或未核取。 工具列按鈕若無法使用也可以關閉，也可以是已核取。

當程式條件以邏輯方式變更時，會更新這些專案的狀態。如果功能表項目產生的命令是由檔所處理，則讓檔更新功能表項目是合理的。 文件可能包含更新所依據的資訊。

如果命令具有多重使用者介面物件 (可能是功能表項目和工具列按鈕)，則兩者都會路由至相同處理函式。 這會在單一位置封裝所有用於相等使用者介面物件的使用者介面更新程式碼。

這個架構會提供用於自動更新使用者介面物件的方便介面。 您可以選擇以其他方法進行更新，不過所提供的介面是有效率且容易使用的。

下列主題說明更新處理常式的使用：

- [呼叫更新處理常式時](when-update-handlers-are-called.md)

- [ON_UPDATE_COMMAND_UI 巨集](on-update-command-ui-macro.md)

- [CCmdUI 類別](the-ccmdui-class.md)

## <a name="see-also"></a>另請參閱

[功能表](menus-mfc.md)

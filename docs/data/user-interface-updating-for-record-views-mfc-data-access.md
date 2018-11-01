---
title: 記錄檢視的使用者介面更新 (MFC 資料存取)
ms.date: 11/04/2016
helpviewer_keywords:
- user interfaces, updating
- menus, updating as context changes
- record views, user interface
ms.assetid: 2c7914b6-2dc3-40c3-b2f2-8371da2a4063
ms.openlocfilehash: 914a262560a10ba4085e0605a0c9f677d7a447fd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50630395"
---
# <a name="user-interface-updating-for-record-views--mfc-data-access"></a>記錄檢視的使用者介面更新 (MFC 資料存取)

`CRecordView` 提供巡覽命令的預設使用者介面更新處理常式。 這些處理常式會自動啟用和停用功能表項目和工具列按鈕等使用者介面物件。 應用程式精靈提供標準功能表和，如果您選擇**可停駐工具列**選項，就會有一組命令工具列按鈕。 如果您使用 `CRecordView` 建立記錄檢視類別，可能需要將類似的使用者介面物件加入應用程式。

### <a name="to-create-menu-resources-with-the-menu-editor"></a>使用功能表編輯器建立功能表資源

1. 參考使用的詳細資訊[功能表編輯器](../windows/menu-editor.md)，使用相同的四個命令建立您自己的功能表。

#### <a name="to-create-toolbar-buttons-with-the-graphics-editor"></a>使用圖形編輯器建立工具列按鈕

1. 參考使用的詳細資訊[工具列編輯器](../windows/toolbar-editor.md)，編輯工具列資源以加入記錄巡覽命令的工具列按鈕。

## <a name="see-also"></a>另請參閱

[支援資料錄檢視的瀏覽](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)<br/>
[使用資料錄檢視](../data/using-a-record-view-mfc-data-access.md)
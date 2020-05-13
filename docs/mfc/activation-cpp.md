---
title: 啟用 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- OLE server applications [MFC], activation
- OLE items [MFC], visual editing
- activation [MFC]
- OLE [MFC], in-place activation
- OLE [MFC], activation
- in-place activation, embedded and linked items
- activating objects
- visual editing, activation
- visual editing
- documents [MFC], OLE
- embedded objects [MFC]
- OLE [MFC], editing
- in-place activation
- activation [MFC], embedded OLE items
- OLE activation [MFC]
ms.assetid: ed8357d9-e487-4aaa-aa6b-2edc4de25dfa
ms.openlocfilehash: 9f3fba71002a19a0be0e3429a0faeeefb7c65197
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354174"
---
# <a name="activation-c"></a>啟用 (C++)

本文介紹了啟動在 OLE 專案的可視化編輯中的角色。 使用者在容器文件中嵌入 OLE 項後,可能需要使用它。 為此,用戶雙擊該專案,該項將激活該專案。 啟動的最常見活動是編輯。 許多當前 OLE 項在啟動以進行編輯時,會導致當前框架視窗中的功能表和工具列發生更改,以反映屬於創建該專案的伺服器應用程式的功能表和工具列。 此行為稱為就地啟動,允許使用者編輯複合文檔中的任何嵌入專案,而無需離開容器文檔的視窗。

還可以在單獨的視窗中編輯嵌入的 OLE 項。 如果容器或伺服器應用程式不支援就地啟動,則會發生這種情況。 在這種情況下,當使用者按兩下嵌入項時,伺服器應用程式在單獨的視窗中啟動,而嵌入的項顯示為其自己的文檔。 使用者在此視窗中編輯項。 編輯完成後,使用者將關閉伺服器應用程式並返回到容器應用程式。

作為替代方法,用戶可以選擇"打開編輯"的物件**\<>"編輯**"功能表上的"打開 **"** 命令。 這將在單獨的視窗中打開物件。

> [!NOTE]
> 在單獨的視窗中編輯嵌入專案是 OLE 版本 1 中的標準行為,某些 OLE 應用程式可能僅支援這種編輯風格。

就地啟動可促進以文檔為中心的文檔創建方法。 用戶可以將複合文檔視為單個實體,無需在應用程式之間切換即可處理它。 但是,就地啟動僅用於嵌入的專案,而不是鏈接專案:它們必須在單獨的視窗中進行編輯。 這是因為連結項實際上存儲在不同的位置。 連結項的編輯在資料的實際上下文中進行,即數據存儲的位置。 在單獨的視窗中編輯連結專案會提醒使用者數據屬於另一個文檔。

MFC 不支援嵌套就地啟動。 如果構建容器/伺服器應用程式,並且該容器/伺服器嵌入到另一個容器中並啟動,則無法就地啟動嵌入其中的物件。

當用戶雙擊時,嵌入項會發生什麼情況取決於為該專案定義的謂詞。 有關詳細資訊,請參閱[啟動:動詞](../mfc/activation-verbs.md)。

## <a name="see-also"></a>另請參閱

[OLE](../mfc/ole-in-mfc.md)<br/>
[容器](../mfc/containers.md)<br/>
[伺服器](../mfc/servers.md)

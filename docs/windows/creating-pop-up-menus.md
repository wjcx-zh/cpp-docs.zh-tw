---
title: 建立快顯功能表 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- context menus [C++], Menu Editor
- pop-up menus [C++], creating
- menus [C++], pop-up
- menus [C++], creating
- shortcut menus [C++], creating
- pop-up menus [C++], displaying
ms.assetid: dff4dddf-2e8d-4c34-b755-90baae426b58
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6c66f7074269e99b35785299800665be48cebef9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415716"
---
# <a name="creating-pop-up-menus-c"></a>建立快顯功能表 （c + +）

[快顯功能表](../mfc/menus-mfc.md) 會顯示常用命令。 它們可隨著指標位置顯示相關內容。 要在您的應用程式中使用快顯功能表，必須建置功能表本身，然後將它連接到應用程式程式碼。

在您建立功能表資源後，您的應用程式程式碼必須載入功能表資源，並使用 [TrackPopupMenu](/windows/desktop/api/winuser/nf-winuser-trackpopupmenu) 讓功能表顯示。 在使用者按一下快顯功能表外部將功能表關閉，或點按命令後，該功能將會恢復。 如果使用者選擇命令，該命令訊息將會傳送至已傳遞控制代碼的視窗。

### <a name="to-create-a-pop-up-menu"></a>建立快顯功能表

1. 以空白的標題 (請不要提供[標題](../windows/creating-a-menu.md) ) **建立功能表**。

2. [將功能表命令加入至新功能表](../windows/adding-commands-to-a-menu.md)。 移至空白功能表標題下方的第一個功能表命令 (暫時標題顯示為 「 `Type Here`)。 輸入 **標題** 和任何其他資訊。

   對快顯功能表中的其他功能表命令重複此程序。

3. 儲存功能表資源。

   > [!TIP]
   > 如需檢視快顯功能表的詳細資訊，請參閱 [以快顯功能表方式檢視功能表](../windows/viewing-a-menu-as-a-pop-up-menu.md)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[將快顯功能表連接至您的應用程式](../windows/connecting-a-pop-up-menu-to-your-application.md)<br/>
[功能表編輯器](../windows/menu-editor.md)
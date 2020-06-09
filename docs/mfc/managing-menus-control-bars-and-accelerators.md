---
title: 管理功能表、控制列和快速鍵
ms.date: 11/04/2016
helpviewer_keywords:
- MDI [MFC], frame windows
- control bars [MFC], updating in frame windows
- menus [MFC], updating as context changes
- user interface objects [MFC], updating
- accelerator tables [MFC]
- sharing menus [MFC]
- updating user-interface objects [MFC]
- frame windows [MFC], updating
- status bars [MFC], updating
ms.assetid: 97ca1997-06df-4373-b023-4f7ecd81047b
ms.openlocfilehash: 9945dc68ffd46bbf5e114a79467299e4b67e3659
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621321"
---
# <a name="managing-menus-control-bars-and-accelerators"></a>管理功能表、控制列和快速鍵

框架視窗管理使用者介面物件的更新，包括功能表、工具列按鈕、狀態列和快速鍵。 也會管理在 MDI 應用程式中共用的功能表列。

## <a name="managing-menus"></a>管理功能表

框架視窗會使用[如何更新使用者介面物件](how-to-update-user-interface-objects.md)中所述的 ON_UPDATE_COMMAND_UI 機制，參與更新使用者介面專案。 工具列和其他控制項列上的按鈕是在閒置迴圈期間更新。 功能表列的下拉式功能表中的功能表項目，會在功能表下拉之前更新。

對於 MDI 應用程式，MDI 框架視窗會管理功能表列和標題。 MDI 框架視窗擁有當沒有現用 MDI 子視窗時用作功能表列的一個預設功能表。 當有使用中的子系時，MDI 框架視窗的功能表列會由現用 MDI 子視窗的功能表接替。 如果 MDI 應用程式支援多個文件類型，例如圖表和工作表文件，則每個類型都會將自己的功能表項目放入功能表列，並且變更主框架視窗的標題。

[CMDIFrameWnd](reference/cmdiframewnd-class.md)會針對 MDI 應用程式所顯示之 [視窗] 功能表上的標準命令，提供預設的執行方式。 尤其是「開新視窗」命令 (ID_WINDOW_NEW) 的實作會在目前文件上建立新的框架視窗和檢視。 只有當您需要進階自訂作業時，才需要覆寫這些實作。

相同文件類型共用功能表資源的多個 MDI 子視窗。 如果數個 MDI 子視窗都是由相同文件範本建立，則可以使用相同功能表資源，以節省 Windows 中的系統資源。

## <a name="managing-the-status-bar"></a>管理狀態列

框架視窗也會將狀態列放置在其工作區內並且管理狀態列的指示器。 框架視窗會視需要清除和更新狀態列中的訊息區域，並在使用者選取功能表項目或工具列按鈕時顯示提示字串，如[如何在狀態列中顯示命令資訊](how-to-display-command-information-in-the-status-bar.md)中所述。

## <a name="managing-accelerators"></a>管理快速鍵

每個框架視窗都會維護選用的快速鍵對應表，可用來自動完成您的鍵盤快速鍵轉譯。 這個機制可讓您輕鬆地定義叫用功能表命令的快速鍵 (也稱為捷徑按鍵)。

## <a name="see-also"></a>另請參閱

[使用框架視窗](using-frame-windows.md)

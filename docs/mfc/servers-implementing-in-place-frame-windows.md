---
title: 伺服器：執行就地框架視窗
ms.date: 09/09/2019
helpviewer_keywords:
- frame windows [MFC], implementing
- OLE server applications [MFC], frame windows
- servers, in-place frame windows
- frame windows [MFC], in-place
- in-place frame windows
ms.assetid: 09bde4d8-15e2-4fba-8d14-9b954d926b92
ms.openlocfilehash: bc5439003b7c891ac3f4000c9b7820746aec4c8d
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907533"
---
# <a name="servers-implementing-in-place-frame-windows"></a>伺服器：執行就地框架視窗

本文說明如果不使用應用程式精靈來建立您的伺服器應用程式，則必須實作自己的視覺化編輯伺服器應用程式的就地框架視窗。 若不遵循本文中所述的程式，您可以從應用程式精靈產生的應用程式或 Visual C++提供的範例，使用現有的就地框架視窗類別。

#### <a name="to-declare-an-in-place-frame-window-class"></a>宣告就地框架視窗類別

1. 從 `COleIPFrameWnd` 衍生就地框架視窗類別。

   - 在您的類別標頭檔中使用 DECLARE_DYNCREATE 宏。

   - 在您的類別執行（.cpp）檔案中使用 IMPLEMENT_DYNCREATE 宏。 如此可讓架構建立此類別物件。

1. 宣告框架視窗類別中的 `COleResizeBar` 成員。 如果您要支援在伺服器應用程式中就地調整大小，就必須如此。

   宣告訊息處理常式（使用[類別 Wizard](reference/mfc-class-wizard.md)），並針對您`Create` `COleResizeBar`的成員呼叫（如果已定義）。 `OnCreate`

1. 如果您有工具列，請在框架視窗類別中宣告 `CToolBar` 成員。

   當伺服器作用中時，請覆寫 `OnCreateControlBars` 成員函式來建立工具列。 例如：

   [!code-cpp[NVC_MFCOleServer#1](../mfc/codesnippet/cpp/servers-implementing-in-place-frame-windows_1.cpp)]

   請參閱步驟 5 之後關於此程式碼的討論。

1. 這包括主要 .cpp 檔案中的就地框架視窗類別標頭檔。

1. 在您的應用程式類別的 `InitInstance` 中，呼叫文件樣板物件的 `SetServerInfo` 函式以指定用來開啟和就地編輯的資源與就地框架視窗。

**If**語句中的函式呼叫系列會從伺服器提供的資源建立工具列。 此時，工具列是容器的視窗階層架構的一部分。 由於這個工具列是衍生自 `CToolBar`，除非您變更擁有者，否則會將其訊息傳遞給至擁有者、容器應用程式的框架視窗。 因此對 `SetOwner` 的呼叫是必要的。 此呼叫會將傳送命令的視窗變更為伺服器的就地框架視窗，使訊息傳遞至伺服器。 如此可讓伺服器回應所提供之工具列的作業。

工具列點陣圖的 ID 應該與在您的伺服器應用程式中所定義的其他就地資源相同。 請[參閱功能表和資源：新增](../mfc/menus-and-resources-server-additions.md)伺服器以取得詳細資料。

如需詳細資訊，請參閱*類別庫參考*中的[coleipframewnd 來衍生](../mfc/reference/coleipframewnd-class.md)、 [COleResizeBar](../mfc/reference/coleresizebar-class.md)和[CDocTemplate：： SetServerInfo](../mfc/reference/cdoctemplate-class.md#setserverinfo) 。

## <a name="see-also"></a>另請參閱

[伺服器](../mfc/servers.md)<br/>
[伺服器：實作伺服器](../mfc/servers-implementing-a-server.md)<br/>
[伺服器：實作伺服器文件](../mfc/servers-implementing-server-documents.md)<br/>
[伺服器：伺服器項目](../mfc/servers-server-items.md)

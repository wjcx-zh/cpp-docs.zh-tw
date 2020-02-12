---
title: 剪貼簿
ms.date: 11/04/2016
helpviewer_keywords:
- cutting and copying data
- copying data
- Clipboard
- Clipboard, programming
- transferring data
ms.assetid: a71b2824-1f14-4914-8816-54578d73ad4e
ms.openlocfilehash: 1db089110904ab88eb9c0c111d9da4e4e6869c82
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127903"
---
# <a name="clipboard"></a>剪貼簿

這系列文章說明如何在 MFC 應用程式中執行 Windows 剪貼簿的支援。 Windows 剪貼簿的使用方式有兩種：

- 執行標準 [編輯] 功能表命令，例如剪下、複製和貼上。

- 使用 OLE 拖放來執行統一的資料傳輸。

剪貼簿是在來源與目的地之間傳送資料的標準 Windows 方法。 它在 OLE 作業中也非常有用。 隨著 OLE 的出現，Windows 中有兩個剪貼簿機制。 標準 Windows 剪貼簿 API 仍然可用，但已使用 OLE 資料傳輸機制進行補充。 OLE 制式資料傳輸（UDT）支援剪下、複製和貼上剪貼簿並拖放。

剪貼簿是整個 Windows 會話共用的系統服務，因此沒有自己的控制碼或類別。 您可以透過[CWnd](../mfc/reference/cwnd-class.md)類別的成員函式來管理剪貼簿。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- [使用每個剪貼簿機制的時機](../mfc/clipboard-when-to-use-each-clipboard-mechanism.md)

- [使用傳統的 Windows 剪貼簿 API](../mfc/clipboard-using-the-windows-clipboard.md)

- [使用 OLE 剪貼簿機制](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)

- [複製和貼上資料](../mfc/clipboard-copying-and-pasting-data.md)

- [新增其他格式](../mfc/clipboard-adding-other-formats.md)

- [Windows 剪貼簿](/windows/win32/dataxchg/clipboard)

- [OLE 拖放](../mfc/drag-and-drop-ole.md)

## <a name="see-also"></a>另請參閱

[使用者介面元素](../mfc/user-interface-elements-mfc.md)

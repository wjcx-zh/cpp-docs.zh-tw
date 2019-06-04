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
ms.openlocfilehash: 5814b2fdfc7fbcaca00037cc64dd71aa27d65cc3
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66504617"
---
# <a name="clipboard"></a>剪貼簿

此系列文章說明如何實作 MFC 應用程式中的 Windows 剪貼簿的支援。 兩種方式使用 Windows 剪貼簿：

- 實作標準編輯功能表命令，例如剪下、 複製和貼。

- 實作統一的資料傳輸使用拖放拖放 (OLE)。

剪貼簿是在來源與目的地之間傳輸資料的標準 Windows 方法。 它也可以在 OLE 作業非常有用。 使用 OLE 的問世，有兩種剪貼簿機制在 Windows 中。 標準的 Windows 剪貼簿 API 仍然可用，但它有已增添 OLE 資料傳輸機制。 OLE 制式資料傳輸 (UDT) 支援剪下、 複製和貼上剪貼簿和拖放。

剪貼簿是共用整個 Windows 工作階段中，因此不需要的控制代碼或類別自己的系統服務。 管理類別成員函式透過剪貼簿[CWnd](../mfc/reference/cwnd-class.md)。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [何時使用每個剪貼簿機制](../mfc/clipboard-when-to-use-each-clipboard-mechanism.md)

- [使用傳統的 Windows 剪貼簿 API](../mfc/clipboard-using-the-windows-clipboard.md)

- [使用 OLE 剪貼簿機制](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)

- [複製並貼上資料](../mfc/clipboard-copying-and-pasting-data.md)

- [加入其他格式](../mfc/clipboard-adding-other-formats.md)

- [Windows 剪貼簿](/windows/desktop/dataxchg/clipboard)

- [實作拖放 (OLE)](../mfc/drag-and-drop-ole.md)

## <a name="see-also"></a>另請參閱

[使用者介面項目](../mfc/user-interface-elements-mfc.md)

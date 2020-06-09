---
title: 剪貼簿：何時使用每個剪貼簿機制
ms.date: 11/04/2016
helpviewer_keywords:
- applications [OLE], Clipboard
- OLE Clipboard, guidelines
- Clipboard [MFC], mechanisms
- OLE Clipboard, formats
- formats [MFC], Clipboard for OLE
- Clipboard [MFC], formats
ms.assetid: fd071996-ef8c-488b-81bd-89057095a201
ms.openlocfilehash: 88fef4b9c0cf37bb475e460c212765b17d4eb634
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625995"
---
# <a name="clipboard-when-to-use-each-clipboard-mechanism"></a>剪貼簿：何時使用每個剪貼簿機制

請在使用剪貼簿時遵循下列指導方針：

- 立即使用 OLE 剪貼簿機制，以在未來啟用新功能。 雖然會維護標準剪貼簿 API，但 OLE 機制是資料傳輸的未來。

- 如果您要撰寫 OLE 應用程式，或您想要有任何 OLE 功能（例如拖放），請使用 OLE 剪貼簿機制。

- 如果您要提供 OLE 格式，請使用 OLE 剪貼簿機制。

## <a name="what-do-you-want-to-do"></a>您想要做什麼

- [使用 OLE 剪貼簿機制](clipboard-using-the-ole-clipboard-mechanism.md)

- [使用 Windows 剪貼簿機制](clipboard-using-the-windows-clipboard.md)

## <a name="see-also"></a>另請參閱

[剪貼簿](clipboard.md)

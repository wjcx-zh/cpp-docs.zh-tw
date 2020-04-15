---
title: SDI 和 MDI
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], SDI applications
- frame windows [MFC], MDI applications
- MFC, windows
- single document interface (SDI) [MFC], applications
- MDI [MFC], vs. SDI
ms.assetid: bb7239d9-4759-4f63-bfff-44a04b48c067
ms.openlocfilehash: 9730e7baf9589c4b05a60703c619aae2e941bdec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372762"
---
# <a name="sdi-and-mdi"></a>SDI 和 MDI

MFC 便於使用單文檔介面 (SDI) 和多文檔介面 (MDI) 應用程式。

SDI 應用程式一次只允許一個打開的文檔框架視窗。 MDI 應用程式允許在應用程式的同一實例中打開多個文檔框架視窗。 MDI 應用程式有一個視窗,其中可以打開多個 MDI 子視窗(即框架視窗本身),每個視窗包含單獨的文檔。 在某些應用程式中,子視窗可以是不同類型的,例如圖表視窗和電子錶格視窗。 在這種情況下,功能表列可以隨著不同類型的 MDI 子視窗的啟動而更改。

> [!NOTE]
> 在 Windows 95 及更高版本下,應用程式通常是 SDI,因為作業系統採用了「以文檔為中心的」視圖。

有關詳細資訊,請參考[文件、檢視和框架](../mfc/documents-views-and-the-framework.md)。

## <a name="see-also"></a>另請參閱

[使用類別來編寫 Windows 應用程式](../mfc/using-the-classes-to-write-applications-for-windows.md)

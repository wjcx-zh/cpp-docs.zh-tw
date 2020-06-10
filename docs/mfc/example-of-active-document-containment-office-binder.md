---
title: 主動式文件內含項目範例：Office 文件夾
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], containers
- examples [MFC], active document containment
- containers [MFC], active document
- active document containers [MFC], examples
- Office Binder [MFC]
- MFC COM, active document containment
ms.assetid: 70dd8568-e8bc-44ac-bf5e-678767efe8e3
ms.openlocfilehash: fe9ccb5b78d9a60c5b8b2a19fe0818a8e1682f00
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623116"
---
# <a name="example-of-active-document-containment-office-binder"></a>主動式文件內含項目範例：Office 文件夾

Microsoft Office Binder 是現用文件容器的範例。 Office Binder 如一般容器一樣包含兩個主要窗格。 左窗格包含對應至 Binder 中的現用文件的圖示。 每份檔都稱為系結器內的一個*區段*。 例如，Binder 可以包含 Word 文件、PowerPoint 檔和 Excel 試算表等等。

按一下左窗格中的圖示可啟動對應的現用文件。 Binder 的右窗格接著會顯示目前所選取現用文件的內容。

如果您開啟並啟動在 Binder 中的 Word 文件，Word 功能表列和工具列會顯示在檢視的頂端，您可以使用所有 Word 命令或工具來編輯文件的內容。 不過，功能表列是 Binder 的功能表列和 Word 的功能表列的組合。 因為 [系結器] 和 [單字] 都有 [說明 **] 功能表，** 所以個別功能表的內容會合並。 活動文檔容器（例如 Office 系結器）會**自動提供 [** 說明] 功能表合併;如需詳細資訊，請參閱說明[功能表合併](help-menu-merging.md)。

當您選取另一個應用程式類型的現用文件時，Binder 的介面會變更為可容納該現用文件的應用程式類型。 例如，如果 Binder 包含 Excel 試算表，則當您選取 Excel 試算表區段時，您會注意到 Binder 中的功能表會變動。

當然，其他類型的容器會在 Binder 旁邊。 [檔案總管] 使用一般的雙窗格介面，其左窗格使用樹狀目錄控制項來顯示磁碟機或網路中的目錄的階層式清單，而右窗格則顯示目前所選取目錄中包含的檔案。 網際網路瀏覽器類型的容器（例如 Microsoft Internet Explorer），而不是使用雙窗格介面，通常會有單一框架，並使用超連結提供導覽。

## <a name="see-also"></a>另請參閱

[主動式文件內含項目](active-document-containment.md)

---
title: 在框架視窗中拖放檔案
ms.date: 11/04/2016
helpviewer_keywords:
- drag and drop [MFC], files
- drag and drop [MFC], File Manager
- Windows Explorer [MFC]
- File Manager drag and drop support [MFC]
- files [MFC], drag and drop
- frame windows [MFC], dragging and dropping files in
- drag and drop [MFC], Windows Explorer
ms.assetid: 85560fe9-121b-4105-bd7b-216b966e19fa
ms.openlocfilehash: 42f21e2441f8ba3d2c6a13503c928880fe100f04
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623162"
---
# <a name="dragging-and-dropping-files-in-a-frame-window"></a>在框架視窗中拖放檔案

框架視窗會管理與檔案總管或檔案管理員的關聯性。

藉由在成員函式的覆寫中加入幾個初始化呼叫 `CWinApp` `InitInstance` （如[CWinApp：應用程式類別](cwinapp-the-application-class.md)中所述），您可以讓框架視窗間接開啟從 [檔案瀏覽器] 或 [檔案管理員] 拖曳並放在框架視窗中的檔案。 請參閱[檔案管理員拖放](special-cwinapp-services.md)。

## <a name="see-also"></a>另請參閱

[使用框架視窗](using-frame-windows.md)

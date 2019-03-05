---
title: 存取檔案狀態
ms.date: 11/04/2016
helpviewer_keywords:
- files [MFC], status information
- examples [MFC], file status
- files [MFC], accessing
- file status [MFC]
- status of files [MFC]
ms.assetid: 1b8891d6-eb0f-4037-a837-4928fe595222
ms.openlocfilehash: 26c263b2d7e4e0243444925cb9416cb337dcd79d
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57298889"
---
# <a name="accessing-file-status"></a>存取檔案狀態

`CFile` 也支援取得檔案狀態，包括檔案是否存在、建立和修改日期和時間、邏輯大小和路徑。

### <a name="to-get-file-status"></a>取得檔案狀態

1. 使用[CFile](../mfc/reference/cfile-class.md)類別來取得和設定檔案的相關的資訊。 一個實用的應用程式是使用`CFile`靜態成員函式**GetStatus**來判斷檔案是否存在。 **GetStatus**會傳回 0，如果指定的檔案不存在。

因此，您可以使用的結果**GetStatus**來判斷是否要使用**cfile:: Modecreate**旗標時開啟的檔案，如下列範例所示：

[!code-cpp[NVC_MFCFiles#3](../atl-mfc-shared/reference/codesnippet/cpp/accessing-file-status_1.cpp)]

如需相關資訊，請參閱[序列化](../mfc/serialization-in-mfc.md)。

## <a name="see-also"></a>另請參閱

[檔案](../mfc/files-in-mfc.md)

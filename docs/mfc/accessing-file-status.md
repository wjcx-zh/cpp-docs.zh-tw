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
ms.openlocfilehash: 23c626940e700d3e9827ef6a7cf849d970e40d5d
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619781"
---
# <a name="accessing-file-status"></a>存取檔案狀態

`CFile` 也支援取得檔案狀態，包括檔案是否存在、建立和修改日期和時間、邏輯大小和路徑。

### <a name="to-get-file-status"></a>取得檔案狀態

1. 使用[CFile](reference/cfile-class.md)類別來取得和設定檔案的相關資訊。 其中一個實用的應用程式是使用 `CFile` 靜態成員函式**GetStatus**來判斷檔案是否存在。 如果指定的檔案不存在， **GetStatus**會傳回0。

因此，您可以使用**GetStatus**的結果來判斷開啟檔案時是否使用**CFile：： modeCreate**旗標，如下列範例所示：

[!code-cpp[NVC_MFCFiles#3](../atl-mfc-shared/reference/codesnippet/cpp/accessing-file-status_1.cpp)]

如需相關資訊，請參閱[序列化](serialization-in-mfc.md)。

## <a name="see-also"></a>另請參閱

[檔案](files-in-mfc.md)

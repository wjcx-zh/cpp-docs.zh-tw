---
title: 關閉檔案
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, file operations
- files [MFC], closing
ms.assetid: 8415a3a8-3c75-45b0-ac2a-d5385f49bdb3
ms.openlocfilehash: 51e51c88260a51ec44f11ecb5c2a88e645194f4e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617238"
---
# <a name="closing-files"></a>關閉檔案

一如在 I/O 作業中，您一旦完成檔案之後，就必須予以關閉。

#### <a name="to-close-a-file"></a>關閉檔案

1. 使用**Close**成員函式。 這個函式會關閉檔案系統檔案，必要時則會清除緩衝區。

如果您在框架上配置了[CFile](reference/cfile-class.md)物件（如[開啟](opening-files.md)檔案中所示的範例），物件將會自動關閉，並在超出範圍時終結。 請注意，刪除 `CFile` 物件並不會刪除檔案系統中的實體檔案。

## <a name="see-also"></a>另請參閱

[檔案](files-in-mfc.md)

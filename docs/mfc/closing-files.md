---
title: 關閉檔案 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, file operations
- files [MFC], closing
ms.assetid: 8415a3a8-3c75-45b0-ac2a-d5385f49bdb3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9c392ef728e1d796a02cfa32edc2c3e8c74d083b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426233"
---
# <a name="closing-files"></a>關閉檔案

一如在 I/O 作業中，您一旦完成檔案之後，就必須予以關閉。

#### <a name="to-close-a-file"></a>關閉檔案

1. 使用**關閉**成員函式。 這個函式會關閉檔案系統檔案，必要時則會清除緩衝區。

如果您將配置[CFile](../mfc/reference/cfile-class.md)框架上的物件 (如所示的範例所示[開啟檔案](../mfc/opening-files.md))，物件就會自動關閉，然後終結它超出範圍時。 請注意，刪除 `CFile` 物件並不會刪除檔案系統中的實體檔案。

## <a name="see-also"></a>另請參閱

[檔案](../mfc/files-in-mfc.md)


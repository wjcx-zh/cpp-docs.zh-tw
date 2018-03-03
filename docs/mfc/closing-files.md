---
title: "關閉檔案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MFC, file operations
- files [MFC], closing
ms.assetid: 8415a3a8-3c75-45b0-ac2a-d5385f49bdb3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 27b1c59c952b022c7382db7d6b2dcb660cca2e9a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="closing-files"></a>關閉檔案
一如在 I/O 作業中，您一旦完成檔案之後，就必須予以關閉。  
  
#### <a name="to-close-a-file"></a>關閉檔案  
  
1.  使用**關閉**成員函式。 這個函式會關閉檔案系統檔案，必要時則會清除緩衝區。  
  
 如果您配置[CFile](../mfc/reference/cfile-class.md)框架上的物件 (如所示的範例所示[開啟檔案](../mfc/opening-files.md))，物件會自動關閉，而且當它超出範圍時終結。 請注意，刪除 `CFile` 物件並不會刪除檔案系統中的實體檔案。  
  
## <a name="see-also"></a>請參閱  
 [檔案](../mfc/files-in-mfc.md)


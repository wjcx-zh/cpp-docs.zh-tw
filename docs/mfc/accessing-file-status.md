---
title: "存取檔案狀態 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- files [MFC], status information
- examples [MFC], file status
- files [MFC], accessing
- file status [MFC]
- status of files [MFC]
ms.assetid: 1b8891d6-eb0f-4037-a837-4928fe595222
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9ff93028c192a735ec75721d3dfdb9929a35edad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="accessing-file-status"></a>存取檔案狀態
`CFile` 也支援取得檔案狀態，包括檔案是否存在、建立和修改日期和時間、邏輯大小和路徑。  
  
### <a name="to-get-file-status"></a>取得檔案狀態  
  
1.  使用[CFile](../mfc/reference/cfile-class.md)類別來取得和設定檔案的相關資訊。 一個實用的應用程式是使用`CFile`靜態成員函式**GetStatus**來判斷檔案是否存在。 **GetStatus**傳回 0，如果指定的檔案不存在。  
  
 因此，您可以使用的結果**GetStatus**來判斷是否要使用**cfile:: Modecreate**旗標時開啟的檔案，如下列範例所示：  
  
 [!code-cpp[NVC_MFCFiles#3](../atl-mfc-shared/reference/codesnippet/cpp/accessing-file-status_1.cpp)]  
  
 如需相關資訊，請參閱[序列化](../mfc/serialization-in-mfc.md)。  
  
## <a name="see-also"></a>請參閱  
 [檔案](../mfc/files-in-mfc.md)


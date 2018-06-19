---
title: 讀取和寫入檔案 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CFile class [MFC], objects
- examples [MFC], reading files
- files [MFC], writing to
- examples [MFC], writing to files
- files [MFC], reading
- MFC, file operations
- CFile class [MFC], reading and writing CFile objects
- reading files
- writing to files [MFC]
ms.assetid: cac0c826-ba56-495f-99b3-ce6336f65763
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 102f5f5de591f8a4475232ad8f0f5383c276e5d1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33347931"
---
# <a name="reading-and-writing-files"></a>讀取和寫入檔案
如果您使用 C 執行階段程式庫檔案處理函式，則會出現熟悉 MFC 讀取和寫入作業。 本文說明直接讀取和寫入直接`CFile`物件。 您可以也不要緩衝處理的檔案 I/O [CArchive](../mfc/reference/carchive-class.md)類別。  
  
#### <a name="to-read-from-and-write-to-the-file"></a>讀取和寫入檔案  
  
1.  使用**讀取**和**寫入**成員函式來讀取和寫入檔案中的資料。  
  
     -或-  
  
2.  `Seek`成員函式也會提供將移到檔案中的特定位移。  
  
 **讀取**接受指標緩衝區和要讀取的位元組數目，並傳回實際讀取的位元組數目。 如果要求的位元組數無法讀取因為檔案結尾 (EOF) 為止，會傳回實際讀取的位元組數目。 如果發生任何讀取的錯誤時，會擲回例外狀況。 **寫入**類似於**讀取**，但不是會傳回寫入的位元組數目。 如果發生寫入錯誤，包括沒有寫入所有指定的位元組，則會擲回例外狀況。 如果您具有有效`CFile`物件，您可以從中讀取或寫入其中，如下列範例所示：  
  
 [!code-cpp[NVC_MFCFiles#2](../atl-mfc-shared/reference/codesnippet/cpp/reading-and-writing-files_1.cpp)]  
  
> [!NOTE]
>  您通常應該執行輸入/輸出作業內**再試一次**/**攔截**例外狀況處理區塊。 如需詳細資訊，請參閱[例外狀況處理 (MFC)](../mfc/exception-handling-in-mfc.md)。  
  
## <a name="see-also"></a>另請參閱  
 [檔案](../mfc/files-in-mfc.md)


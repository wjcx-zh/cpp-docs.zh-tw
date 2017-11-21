---
title: "例外狀況： 檢查例外狀況內容 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- exception handling [MFC], MFC
- try-catch exception handling [MFC], MFC function exceptions
- catch blocks, MFC function exceptions
- CException class [MFC], class exceptions
- try-catch exception handling [MFC], exception contents
- throwing exceptions [MFC], exception contents
ms.assetid: dfda4782-b969-4f60-b867-cc204ea7f33a
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 06d33c021d5bb7e802a9aba362fcd0152ff5eab0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="exceptions-examining-exception-contents"></a>例外狀況：檢查例外狀況內容
雖然**攔截**區塊的引數可以是幾乎任何資料類型，MFC 函式會擲回例外狀況衍生自類別類型的`CException`。 若要攔截 MFC 函式所擲回例外狀況，接著，您撰寫**攔截**其引數是指標的區塊來`CException`物件 (或物件衍生自`CException`，例如`CMemoryException`)。 根據例外狀況的確切類型，您可以檢查例外狀況物件的資料成員，來收集例外狀況特定原因的相關資訊。  
  
 例如，`CFileException`類型具有`m_cause`資料成員，其中包含指定的檔案例外狀況原因的列舉的類型。 可能的一些範例傳回值為**CFileException::fileNotFound**和**CFileException::readOnly**。  
  
 下列範例示範如何檢查的內容`CFileException`。 其他例外狀況型別可以同樣地檢查。  
  
 [!code-cpp[NVC_MFCExceptions#13](../mfc/codesnippet/cpp/exceptions-examining-exception-contents_1.cpp)]  
  
 如需詳細資訊，請參閱[例外狀況： 例外狀況時釋放物件](../mfc/exceptions-freeing-objects-in-exceptions.md)和[例外狀況： 攔截及刪除例外狀況](../mfc/exceptions-catching-and-deleting-exceptions.md)。  
  
## <a name="see-also"></a>另請參閱  
 [例外狀況處理](../mfc/exception-handling-in-mfc.md)


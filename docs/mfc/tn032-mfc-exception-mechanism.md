---
title: "TN032: MFC 例外狀況機制 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.exceptions
dev_langs:
- C++
helpviewer_keywords:
- TN032
- MFC, exceptions
- CException class [MFC], using
ms.assetid: 0271f0aa-82cb-47a2-b7ea-e88126fc7e43
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bf82d4b158cedd2d8f6916dfb01d26db6c62d83b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="tn032-mfc-exception-mechanism"></a>TN032：MFC 例外狀況機制
舊版的 Visual c + + 不支援標準 c + + 例外狀況機制，MFC 提供巨集**TRY/CATCH/THROW**所使用。 此版本的 Visual C++ 完全支援 C++ 例外狀況。 此提示涵蓋先前巨集的一些進階實作詳細資料，包括如何自動清除堆疊式物件。 因為 C++ 例外狀況預設支援堆疊回溯，因此這個技術提示不再是必要的。  
  
 請參閱[例外狀況： 使用 MFC 巨集和 c + + 例外狀況](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)如需有關 MFC 巨集和新的 c + + 關鍵字之間的差異。  
  
## <a name="see-also"></a>請參閱  
 [依數字的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)


---
title: "CString Exception Cleanup | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CString objects, 例外狀況"
  - "例外狀況處理, cleanup code"
ms.assetid: 28b9ce70-be63-4a0d-92a8-44bbfbc95e83
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# CString Exception Cleanup
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在舊版的 MFC 中，請務必先清除物件使用 [CString](../atl-mfc-shared/reference/cstringt-class.md) 之後。  MFC 3.0 版和以後，明確清除不再是必要的。  
  
 在 MFC 中使用的 C\+\+ 例外狀況處理機制下，您不需要擔心清除例外狀況之後。  如需說明如何 C\+\+ 「回溯」堆疊，攔截例外狀況後，請參閱 [嘗試、擷取和 throw 陳述式](../cpp/try-throw-and-catch-statements-cpp.md)。  即使您使用 MFC **TRY**\/**CATCH** 巨集而不是 C\+\+ 關鍵字 **try** 和 **catch**， MFC 底使用 C\+\+ 例外狀況機制，如此一來，並且不需要明確地清除。  
  
## 請參閱  
 [字串](../atl-mfc-shared/strings-atl-mfc.md)   
 [例外狀況處理](../mfc/exception-handling-in-mfc.md)
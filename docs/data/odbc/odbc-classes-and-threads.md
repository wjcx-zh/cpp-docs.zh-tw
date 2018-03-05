---
title: "ODBC 類別和執行緒 |Microsoft 文件"
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
- ODBC classes, and threads
- ODBC, multithreaded applications
- threading [MFC], ODBC support
ms.assetid: 16543926-7331-41a6-ba50-72288f2a61b7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1d1d922dfc34fa3e5530eca77a6501ad3e331fc8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="odbc-classes-and-threads"></a>ODBC 類別和執行緒
從 MFC 4.2 開始，沒有多執行緒 MFC ODBC 類別的支援。 不過請注意，MFC 不提供多執行緒支援適用於 DAO 類別。  
  
 ODBC 類別的多執行緒支援有一些限制。 這些類別會包裝 ODBC API，因為它們會限制為元件建立所在的多執行緒的支援。 比方說，許多 ODBC 驅動程式不是安全執行緒，因此，MFC ODBC 類別不具備執行緒安全如果您使用它們其中一個驅動程式。 您應該確認您的特定驅動程式是否具備執行緒安全。  
  
 在建立多執行緒應用程式時，您應該非常小心使用多執行緒管理相同物件中。 例如，使用相同`CRecordset`兩個執行緒中的物件可能會造成問題，擷取資料時，提取作業在一個執行緒可能會覆寫另一個執行緒所提取的資料。 MFC ODBC 類別不同的執行緒中的常見用法是共用開啟`CDatabase`多個相同的 ODBC 連接使用個別執行緒物件`CRecordset`中每個執行緒的物件。 請注意，您應該傳遞未開啟`CDatabase`物件`CRecordset`另一個執行緒的物件。  
  
> [!NOTE]
>  如果您必須擁有管理相同物件的多個執行緒，則應該實作適當的同步處理機制，例如關鍵區段。 請注意，某些作業，例如**開啟**，未受保護。 您應該確定這些作業將不會同時從呼叫個別的執行緒。  
  
 如需有關建立多執行緒應用程式的詳細資訊，請參閱[多執行緒主題](../../parallel/multithreading-support-for-older-code-visual-cpp.md)。  
  
## <a name="see-also"></a>請參閱  
 [開放式資料庫連接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)   
 [資料存取程式設計 (MFC/ATL)](../../data/data-access-programming-mfc-atl.md)
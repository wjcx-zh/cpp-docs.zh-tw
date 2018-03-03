---
title: "TN047： 放寬資料庫異動需求 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.data
dev_langs:
- C++
helpviewer_keywords:
- TN047
ms.assetid: f93c51cf-a8c0-43d0-aa47-7bcb8333d693
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 92631d96e8782a80275695ef4bf2623dc1bff833
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="tn047-relaxing-database-transaction-requirements"></a>TN047：放寬資料庫異動需求
這個技術提示討論 MFC ODBC 資料庫類別的交易需求，現在已過時。 在 MFC 4.2 之前的資料庫類別所需資料指標會保留在資料錄集之後**CommitTrans**或**復原**作業。 ODBC 驅動程式和 DBMS 並不支援此層級的資料指標保留，如果資料庫類別未啟用交易。  
  
 從 MFC 4.2 開始，資料庫類別有放寬需要資料指標保留的限制。 如果驅動程式支援，將會啟用交易。 不過，您現在必須檢查的效果**CommitTrans**或**復原**上開啟資料錄集的作業。 請參閱成員函式[CDatabase::GetCursorCommitBehavior](../mfc/reference/cdatabase-class.md#getcursorcommitbehavior)和[CDatabase::GetCursorRollbackBehavior](../mfc/reference/cdatabase-class.md#getcursorrollbackbehavior)如需詳細資訊。  
  
## <a name="see-also"></a>請參閱  
 [依數字的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)


---
title: 選取和操作資料錄 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- records, selecting
- record selection, MFC ODBC classes
- ODBC recordsets, selecting records
ms.assetid: 7f0b3a4a-9941-4475-a612-9ec8d15b7691
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2a4b76d0b4273e5afb32206336b4aabbfe9294eb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="selecting-and-manipulating-records"></a>選取和操作資料錄
通常當您選取的記錄從資料來源，使用 SQL**選取**陳述式中，您取得結果集，也就是一組從資料表或查詢記錄。 資料庫類別中，您可以使用資料錄集物件選取，然後存取該結果集。 這是衍生自類別的特定應用程式類別的物件[CRecordset](../../mfc/reference/crecordset-class.md)。 當您定義的資料錄集類別時，您可以指定要將它與相關聯的資料來源、 使用，資料表和資料表的資料行。 MFC 應用程式精靈或**加入類別**(中所述[加入 MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) 與特定資料來源的連接，建立一個類別。 精靈寫入[GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql)類別成員函式`CRecordset`傳回資料表的名稱。 如需有關如何使用精靈來建立資料錄集類別的詳細資訊，請參閱[MFC 應用程式精靈、 資料庫支援](../../mfc/reference/database-support-mfc-application-wizard.md)和[加入 MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)。  
  
 使用[CRecordset](../../mfc/reference/crecordset-class.md)物件在執行階段，您可以：  
  
-   檢查目前的資料錄的資料欄位。  
  
-   篩選或排序資料錄集。  
  
-   自訂預設 SQL**選取**陳述式。  
  
-   捲動以選取的記錄。  
  
-   加入、 更新或刪除資料錄 （如果資料來源和資料錄集是可更新）。  
  
-   測試是否資料錄集可讓重新查詢並重新整理資料錄集的內容。  
  
 當您完成使用資料錄集物件時，您可以關閉並終結。 如需有關資料錄集的詳細資訊，請參閱[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)。  
  
## <a name="see-also"></a>另請參閱  
 [ODBC 和 MFC](../../data/odbc/odbc-and-mfc.md)
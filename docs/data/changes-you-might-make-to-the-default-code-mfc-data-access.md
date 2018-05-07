---
title: 您可能對預設程式碼 （MFC 資料存取） 變更 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- record views [C++], customizing default code
ms.assetid: 9992ed37-a6bf-45a5-a572-5c14e42b6628
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e647f6350819fa2cccb5f8319f95fbac16ca19fc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="changes-you-might-make-to-the-default-code--mfc-data-access"></a>您可能對預設程式碼所做的變更 (MFC 資料存取)
[MFC 應用程式精靈](../mfc/reference/database-support-mfc-application-wizard.md)寫入您選取單一資料表中的所有記錄的資料錄集類別。 您經常會想要以下列一種或多種方式修改該行為：  
  
-   設定資料錄集的篩選條件或排序順序。 這樣在`OnInitialUpdate`資料錄集物件之前建構之後其**開啟**呼叫成員函式。 如需詳細資訊，請參閱[資料錄集： 篩選資料錄 (ODBC)](../data/odbc/recordset-filtering-records-odbc.md)和[資料錄集： 排序資料錄 (ODBC)](../data/odbc/recordset-sorting-records-odbc.md)。  
  
-   參數化資料錄集。 請在篩選之後指定實際的執行階段參數值。 如需詳細資訊，請參閱[資料錄集： 參數化資料錄集 (ODBC)](../data/odbc/recordset-parameterizing-a-recordset-odbc.md)  
  
-   傳遞至自訂的 SQL 字串[開啟](../mfc/reference/crecordset-class.md#open)成員函式。 如需您可以使用這項技術完成的討論，請參閱[SQL： 自訂資料錄集的 SQL 陳述式 (ODBC)](../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用資料錄檢視](../data/using-a-record-view-mfc-data-access.md)
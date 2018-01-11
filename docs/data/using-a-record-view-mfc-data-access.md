---
title: "使用資料錄檢視 （MFC 資料存取） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: record views, customizing default code
ms.assetid: 91f2828f-0666-4273-ae28-e4703fd98521
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 18d3b4b36d63013fcb5e3762f96e5970644cbff0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="using-a-record-view--mfc-data-access"></a>使用記錄檢視 (MFC 資料存取)
本主題說明通常如何自訂精靈為您撰寫的資料錄檢視的預設程式碼。 一般而言，在您想要限制與資料錄選取[篩選](../data/odbc/recordset-filtering-records-odbc.md)或[參數](../data/odbc/recordset-parameterizing-a-recordset-odbc.md)，也或許是[排序](../data/odbc/recordset-sorting-records-odbc.md)資料錄、 自訂 SQL 陳述式。  
  
 使用`CRecordView`是就如同使用[CFormView](../mfc/reference/cformview-class.md)。 基本方法是使用資料錄檢視顯示甚或更新單一資料錄集的記錄。 此外，您可以使用其他資料錄集，以及，討論[資料錄檢視： 填入清單方塊從第二個資料錄集](../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md)。  
  
## <a name="see-also"></a>請參閱  
 [資料錄檢視 （MFC 資料存取）](../data/record-views-mfc-data-access.md)   
 [ODBC 驅動程式清單](../data/odbc/odbc-driver-list.md)
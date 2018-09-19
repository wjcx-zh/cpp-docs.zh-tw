---
title: 使用資料錄檢視 （MFC 資料存取） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- record views, customizing default code
ms.assetid: 91f2828f-0666-4273-ae28-e4703fd98521
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4107b5e19020843fa50495153841ebcba64301ad
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077681"
---
# <a name="using-a-record-view--mfc-data-access"></a>使用記錄檢視 (MFC 資料存取)

本主題說明通常如何自訂精靈為您撰寫的資料錄檢視的預設程式碼。 通常，您想要限制記錄的選取範圍與[篩選器](../data/odbc/recordset-filtering-records-odbc.md)或是[參數](../data/odbc/recordset-parameterizing-a-recordset-odbc.md)，也或許是[排序](../data/odbc/recordset-sorting-records-odbc.md)資料錄、 自訂 SQL 陳述式。  
  
使用`CRecordView`是與使用大致相同[CFormView](../mfc/reference/cformview-class.md)。 基本方法是使用資料錄檢視顯示甚或更新單一資料錄集的記錄。 除此之外，您可能想要其他的資料錄集也中所述[資料錄檢視： 填入清單方塊從第二個資料錄集](../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md)。  
  
## <a name="see-also"></a>另請參閱  

[資料錄檢視 (MFC 資料存取)](../data/record-views-mfc-data-access.md)<br/>
[ODBC 驅動程式清單](../data/odbc/odbc-driver-list.md)
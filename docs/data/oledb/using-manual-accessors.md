---
title: "使用手動存取子 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- command handling, OLE DB Templates
- manual accessors
- accessors [C++], manual
ms.assetid: 29f00a89-0240-482b-8413-4120b9644672
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e7d6bd8f0228103e4899e6bc24f6d67af0f3fdb4
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="using-manual-accessors"></a>使用手動存取子
有四個項目時處理未知的命令：  
  
-   判斷參數  
  
-   執行命令  
  
-   決定輸出資料行  
  
-   查看是否有多個傳回的資料列集  
  
 若要使用 OLE DB 消費者範本這樣做，請使用`CManualAccessor`類別，並遵循下列步驟：  
  
1.  開啟`CCommand`物件`CManualAccessor`做為範本參數。  
  
    ```  
    CCommand<CManualAccessor, CRowset, CMultipleResults> rs;  
    ```  
  
2.  查詢的工作階段**IDBSchemaRowset**介面，並且使用程序參數的資料列集。 如果**IDBSchemaRowset**介面，則無法使用查詢`ICommandWithParameters`介面。 呼叫`GetParameterInfo`資訊。 如果沒有介面可供使用，您可以假設沒有任何參數。  
  
3.  針對每個參數，呼叫`AddParameterEntry`加入參數，並加以設定。  
  
4.  開啟資料列集，但將繫結參數設定為**false**。  
  
5.  呼叫`GetColumnInfo`来擷取之輸出資料行。 使用`AddBindEntry`將輸出資料行新增至繫結。  
  
6.  呼叫`GetNextResult`來判斷是否可以使用多個資料列集。 重複步驟 2 至 5。  
  
 如需手動存取子的範例，請參閱**CDBListView::CallProcedure**中[DBVIEWER](http://msdn.microsoft.com/en-us/07620f99-c347-4d09-9ebc-2459e8049832)範例。  
  
## <a name="see-also"></a>請參閱  
 [使用存取子](../../data/oledb/using-accessors.md)
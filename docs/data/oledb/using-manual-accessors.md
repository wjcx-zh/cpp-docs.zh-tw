---
title: 使用手動存取子 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- command handling, OLE DB Templates
- manual accessors
- accessors [C++], manual
ms.assetid: 29f00a89-0240-482b-8413-4120b9644672
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5aa7f72cc76f80e2304faf93ca0c6198c505e88a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46101636"
---
# <a name="using-manual-accessors"></a>使用手動存取子

有四個項目時處理未知的命令：  
  
- 判斷參數  
  
- 執行命令  
  
- 決定輸出資料行  
  
- 看看是否有多個傳回的資料列集  
  
若要使用 OLE DB 消費者範本這樣做，請使用`CManualAccessor`類別，並遵循下列步驟：  
  
1. 開啟`CCommand`物件`CManualAccessor`做為範本參數。  
  
    ```cpp  
    CCommand<CManualAccessor, CRowset, CMultipleResults> rs;  
    ```  
  
1. 查詢的工作階段`IDBSchemaRowset`介面，並使用程序參數的資料列集。 如果`IDBSchemaRowset`介面，則無法使用查詢`ICommandWithParameters`介面。 呼叫`GetParameterInfo`的資訊。 如果兩個介面都可用，您可以假設沒有任何參數。  
  
1. 針對每個參數，呼叫`AddParameterEntry`，將參數加入並設定它們。  
  
1. 開啟資料列集，但將繫結參數設定為**false**。  
  
1. 呼叫`GetColumnInfo`来擷取之輸出資料行。 使用`AddBindEntry`將輸出資料行新增至繫結。  
  
1. 呼叫`GetNextResult`，判斷是否可以使用多個資料列集。 重複步驟 2 至 5。  
  
如需手動存取子的範例，請參閱 <<c0> `CDBListView::CallProcedure` 中[DBVIEWER](https://github.com/Microsoft/VCSamples)範例。  
  
## <a name="see-also"></a>另請參閱  

[使用存取子](../../data/oledb/using-accessors.md)
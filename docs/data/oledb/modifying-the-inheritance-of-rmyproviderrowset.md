---
title: "修改 RMyProviderRowset 的繼承 |Microsoft 文件"
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
- RMyProviderRowset
- inheritance [C++]
ms.assetid: 33089c90-98a4-43e7-8e67-d4bb137e267e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f63e13b36f723decab9c5886b0523454d7c26fd7
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="modifying-the-inheritance-of-rmyproviderrowset"></a>修改 RMyProviderRowset 的繼承
若要加入`IRowsetLocate`介面的簡單唯讀提供者範例，請修改繼承的**RMyProviderRowset**。 一開始， **RMyProviderRowset**繼承自`CRowsetImpl`。 您需要修改它繼承自**CRowsetBaseImpl**。  
  
 若要這樣做，建立新的類別， `CMyRowsetImpl`，MyProviderRS.h 中：  
  
```cpp
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
  
template <class T, class Storage, class CreatorClass, class ArrayType = CAtlArray<Storage>>  
class CMyRowsetImpl:  
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType, CSimpleRow, IRowsetLocateImpl< T, IRowsetLocate >>  
{  
...  
};  
```  
  
 現在，編輯，如下所示為 MyProviderRS.h 中的 COM 介面對應：  
  
```  
BEGIN_COM_MAP(CMyRowsetImpl)  
   COM_INTERFACE_ENTRY(IRowsetLocate)  
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)  
END_COM_MAP()  
```  
  
 這會建立會告知 COM 介面對應`CMyRowsetImpl`呼叫**QueryInterface**兩者`IRowset`和`IRowsetLocate`介面。 若要取得所有的其他資料列集的實作類別，對應連結`CMyRowsetImpl`類別回**CRowsetBaseImpl** OLE DB 範本所定義的類別，則為對應使用 COM_INTERFACE_ENTRY_CHAIN 巨集，它會告訴若要掃描的 COM OLE DB 樣板中的對應**CRowsetBaseImpl**回應`QueryInterface`呼叫。  
  
 最後，連結`RAgentRowset`至`CMyRowsetBaseImpl`藉由修改`RAgentRowset`繼承自`CMyRowsetImpl`、，如下所示：  
  
```  
class RAgentRowset : public CMyRowsetImpl<RAgentRowset, CAgentMan, CMyProviderCommand>  
```  
  
 `RAgentRowset` 現在可以使用`IRowsetLocate`同時利用其餘部分的資料列集類別實作的介面。  
  
 完成此動作後，您可以[動態決定傳回給消費者的資料行](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md)。  
  
## <a name="see-also"></a>請參閱  
 [增強簡單唯讀提供者](../../data/oledb/enhancing-the-simple-read-only-provider.md)
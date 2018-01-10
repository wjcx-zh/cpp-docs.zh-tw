---
title: "CNoRowset 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CNoRowset
- ATL::CNoRowset<TAccessor>
- CNoRowset
- ATL.CNoRowset<TAccessor>
- ATL::CNoRowset
dev_langs: C++
helpviewer_keywords: CNoRowset class
ms.assetid: 55c6c7a4-9e3a-4775-a2dd-c8b333012fa6
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 901d857b5095dd882a368b9a87e8a7d38d20bc42
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cnorowset-class"></a>CNoRowset 類別
可用來當做範本引數 (`TRowset`) 的[CCommand](../../data/oledb/ccommand-class.md)或[CTable](../../data/oledb/ctable-class.md)。  
  
## <a name="syntax"></a>語法  
  
```  
template <class TAccessor = CAccessorBase>  
class CNoRowset  
```  
  
#### <a name="parameters"></a>參數  
 `TAccessor`  
 存取子類別。 預設值為 `CAccessorBase`。  
  
## <a name="remarks"></a>備註  
 使用`CNoRowset`作為範本引數，如果命令未傳回資料列集。  
  
 `CNoRowset`會實作下列的虛設常式方法，其中每一個都對應至其他存取子類別的方法：  
  
-   **BindFinished** -表示當繫結完成時 (傳回`S_OK`)。  
  
-   **關閉**-釋放資料列和目前的 IRowset 介面。  
  
-   `GetIID`-擷取連接點的介面 ID。  
  
-   **GetInterface** -擷取介面。  
  
-   `GetInterfacePtr`-擷取封裝的介面指標。  
  
-   **SetAccessor** -設定存取子的指標。  
  
-   **SetupOptionalRowsetInterfaces** -設定選擇性的資料列集介面。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)
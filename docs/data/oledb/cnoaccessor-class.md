---
title: "CNoAccessor 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CNoAccessor
- CNoAccessor
- ATL.CNoAccessor
dev_langs: C++
helpviewer_keywords: CNoAccessor class
ms.assetid: eb669ae5-0a56-49a3-9646-c4ae6239da31
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 799fe151b22748da25901139a5aefe67460b2484
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cnoaccessor-class"></a>CNoAccessor 類別
可用來當做範本引數 (`TAccessor`) 範本的類別，例如`CCommand`和`CTable`，需要的引數存取子類別。  
  
## <a name="syntax"></a>語法  
  
```  
class CNoAccessor  
```  
  
## <a name="remarks"></a>備註  
 使用`CNoAccessor`作為範本引數時，您不想要支援的參數或輸出資料行的類別。  
  
 `CNoAccessor`會實作下列的虛設常式方法，其中每一個都對應至其他存取子類別的方法：  
  
-   **BindColumns** -繫結至存取子的資料行。  
  
-   `BindParameters`-將繫結的建立的參數的資料行。  
  
-   **繫結**-建立繫結。  
  
-   **關閉**-關閉存取子。  
  
-   `ReleaseAccessors`-釋放存取子類別建立的。  
  
-   `FreeRecordMemory`-會釋出不再需要將目前記錄中的任何資料行。  
  
-   `GetColumnInfo`-從開啟的資料列集取得資料行資訊。  
  
-   `GetNumAccessors`-擷取類別所建立的存取子的數目。  
  
-   `IsAutoAccessor`-如果資料自動擷取存取子在移動操作傳回 true。  
  
-   `GetHAccessor`-擷取指定的存取子的存取子控制代碼。  
  
-   `GetBuffer`-擷取書籤緩衝區的指標。  
  
-   **NoBindOnNullRowset** -可防止在空白資料列集上的資料繫結。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)
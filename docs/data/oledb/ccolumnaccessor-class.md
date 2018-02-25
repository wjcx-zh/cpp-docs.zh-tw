---
title: "CColumnAccessor 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CColumnAccessor
- ATL::CColumnAccessor
- ATL.CColumnAccessor
dev_langs:
- C++
helpviewer_keywords:
- CColumnAccessor class
ms.assetid: 6ce1e67f-6a20-490d-9326-c168b43eee7e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fa03f7ee652ee176c7333ac5ef4e264b7f4d5cf8
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="ccolumnaccessor-class"></a>CColumnAccessor 類別
產生插入的消費者程式碼。  
  
## <a name="syntax"></a>語法

```cpp
class CColumnAccessor : public CAccessorBase  
```  
  
## <a name="remarks"></a>備註  
 插入程式碼中，每個資料行繫結為個別的存取子。 您應該注意在插入程式碼會使用這個類別 （例如，您可能會遇到它進行偵錯時），但您通常不必直接使用它或它的方法。  
  
 `CColumnAccessor` 會實作下列的虛設常式方法，其中每一個都對應到其他存取子類別方法的功能：  
  
-   `CColumnAccessor` 建構函式。執行個體化並初始化`CColumnAccessor`物件。  
  
-   `CreateAccessor` 資料行繫結結構配置記憶體並初始化的資料行的資料成員。  
  
-   **BindColumns**至存取子繫結資料行。  
  
-   **SetParameterBuffer**參數用來配置緩衝區。  
  
-   `AddParameter` 將參數項目加入至參數項目結構。  
  
-   **HasOutputColumns**判斷存取子是否有輸出資料行  
  
-   **HasParameters**判斷存取子是否有參數。  
  
-   `BindParameters` 將建立的參數繫結至資料行。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)
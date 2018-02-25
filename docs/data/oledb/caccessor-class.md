---
title: "CAccessor 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CAccessor<T>
- ATL::CAccessor
- CAccessor
- ATL::CAccessor<T>
- ATL.CAccessor
dev_langs:
- C++
helpviewer_keywords:
- CAccessor class
ms.assetid: b2ba959f-a686-46f3-8837-176248aef748
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1f0e893f300b7d89bee14ce28490328979d0fa17
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="caccessor-class"></a>CAccessor 類別
代表其中一個存取子類型。  
  
## <a name="syntax"></a>語法  
  
```  
  
template <class T>  
class CAccessor : public CAccessorBase, public T  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 使用者記錄類別。  
  
## <a name="remarks"></a>備註  
 記錄以靜態方式繫結至資料來源時使用它。 記錄包含緩衝區。 這個類別支援多個存取子資料列集。  
  
 當您知道結構和資料庫類型時，請使用此存取子類型。  
  
 如果您的存取子包含指向記憶體中的欄位 (例如`BSTR`或介面)，必須釋出，呼叫成員函式[caccessorrowset:: Freerecordmemory](../../data/oledb/caccessorrowset-freerecordmemory.md)下一步 再讀取記錄。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)
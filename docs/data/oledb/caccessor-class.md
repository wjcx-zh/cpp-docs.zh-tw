---
title: CAccessor 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9e7f722d4d1759bdec7a23bb15076b38de000eb6
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2018
ms.locfileid: "39337413"
---
# <a name="caccessor-class"></a>CAccessor 類別
代表其中一個存取子類型。  
  
## <a name="syntax"></a>語法  
  
```cpp
template <class T>  
class CAccessor : public CAccessorBase, public T  
```  
  
### <a name="parameters"></a>參數  
 *T*  
 使用者記錄類別。  
  
## <a name="remarks"></a>備註  
 它是用來記錄以靜態方式繫結至資料來源。 記錄包含緩衝區。 此類別支援多個存取子資料列集。  
  
 當您知道結構和資料庫類型時，請使用這個存取子類型。  
  
 如果您的存取子包含指向的記憶體的欄位 (例如`BSTR`或介面)，必須釋出，呼叫成員函式[caccessorrowset:: Freerecordmemory](../../data/oledb/caccessorrowset-freerecordmemory.md)下一步 再讀取記錄。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)
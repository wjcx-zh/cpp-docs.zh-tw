---
title: 'Irowsetimpl:: Createrow |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetImpl.CreateRow
- ATL.IRowsetImpl.CreateRow
- ATL::IRowsetImpl::CreateRow
- CreateRow
- IRowsetImpl::CreateRow
dev_langs:
- C++
helpviewer_keywords:
- CreateRow method
ms.assetid: b01c430c-9484-4fef-a6cf-a2e8d9d99130
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: eae3fbdce1db5760d4ee5ca75e007c01e98b7bed
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33103238"
---
# <a name="irowsetimplcreaterow"></a>IRowsetImpl::CreateRow
所呼叫的 helper 方法[GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md)配置新**HROW**。  
  
## <a name="syntax"></a>語法  
  
```
HRESULT CreateRow(DBROWOFFSET lRowsOffset,  
  DBCOUNTITEM& cRowsObtained,  
   HROW* rgRows);  
```  
  
#### <a name="parameters"></a>參數  
 *lRowsOffset*  
 正在建立的資料列的資料指標位置。  
  
 *cRowsObtained*  
 傳回給使用者指出建立的資料列數，傳遞的參考。  
  
 *rgRows*  
 陣列**HROW**傳回給呼叫者以新建立的資料列控點。  
  
## <a name="remarks"></a>備註  
 如果資料列存在，這個方法會呼叫[AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md)並傳回。 否則，會配置 RowClass 樣板變數的新執行個體，並將它加入[m_rgRowHandles](../../data/oledb/irowsetimpl-m-rgrowhandles.md)。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>另請參閱  
 [IRowsetImpl 類別](../../data/oledb/irowsetimpl-class.md)
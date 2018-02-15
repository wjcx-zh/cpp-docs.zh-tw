---
title: "Irowsetimpl:: Createrow |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4403388146b79eec4435374793b2517dd46ff188
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
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
  
## <a name="see-also"></a>請參閱  
 [IRowsetImpl 類別](../../data/oledb/irowsetimpl-class.md)
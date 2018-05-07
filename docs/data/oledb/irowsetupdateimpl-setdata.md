---
title: 'Irowsetupdateimpl:: Setdata |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- SetData
- IRowsetUpdateImpl::SetData
- IRowsetUpdateImpl.SetData
- ATL::IRowsetUpdateImpl::SetData
- ATL.IRowsetUpdateImpl.SetData
dev_langs:
- C++
helpviewer_keywords:
- SetData method
ms.assetid: 7288a8d1-a7cf-4957-b832-0f3b18fd0da4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: adb15394f4470e23c0ecec2e704829c973c7f3a9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="irowsetupdateimplsetdata"></a>IRowsetUpdateImpl::SetData
設定一或多個資料行中的資料值。  
  
## <a name="syntax"></a>語法  
  
```cpp
      STDMETHOD (SetData )(HROW hRow,  
   HACCESSOR hAccessor,  
   void* pSrcData);  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[irowsetchange:: Setdata](https://msdn.microsoft.com/en-us/library/ms721232.aspx)中*OLE DB 程式設計人員參考*。  
  
## <a name="remarks"></a>備註  
 這個方法會覆寫[irowsetchangeimpl:: Setdata](../../data/oledb/irowsetchangeimpl-setdata.md)方法，但包括原始資料，以允許立即或延遲處理作業的快取。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>另請參閱  
 [IRowsetUpdateImpl 類別](../../data/oledb/irowsetupdateimpl-class.md)
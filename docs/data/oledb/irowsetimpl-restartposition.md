---
title: 'Irowsetimpl:: Restartposition |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IRowsetImpl.RestartPosition
- IRowsetImpl::RestartPosition
- RestartPosition
- ATL::IRowsetImpl::RestartPosition
- IRowsetImpl.RestartPosition
dev_langs:
- C++
helpviewer_keywords:
- RestartPosition method
ms.assetid: 14de66ef-8d2c-4404-adb6-3f6c74ac6cf1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1c203cc19e31f22df5903f099e953fcf5663718f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="irowsetimplrestartposition"></a>IRowsetImpl::RestartPosition
重新定位下一個提取位置，為其初始位置。也就是說，它的位置，第一個資料列集時建立。  
  
## <a name="syntax"></a>語法  
  
```cpp
      STDMETHOD(RestartPosition )(HCHAPTER /* hReserved */);  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[irowset:: Restartposition](https://msdn.microsoft.com/en-us/library/ms712877.aspx)中*OLE DB 程式設計人員參考*。  
  
## <a name="remarks"></a>備註  
 是之前未定義的資料列集定位**getnextrow 時發生**呼叫。 您可以移動 rowet 中藉由呼叫`RestartPosition`然後提取或捲動回溯。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>另請參閱  
 [IRowsetImpl 類別](../../data/oledb/irowsetimpl-class.md)
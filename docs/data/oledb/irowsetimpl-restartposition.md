---
title: "Irowsetimpl:: Restartposition |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c42e3685f1d857d60a4586544bf01a8a7d09f011
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
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
  
## <a name="see-also"></a>請參閱  
 [IRowsetImpl 類別](../../data/oledb/irowsetimpl-class.md)
---
title: "IConvertTypeImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.IConvertTypeImpl<T>
- IConvertTypeImpl
- ATL.IConvertTypeImpl
- ATL::IConvertTypeImpl
- ATL::IConvertTypeImpl<T>
dev_langs:
- C++
helpviewer_keywords:
- IConvertTypeImpl class
ms.assetid: 7f81e79e-7d3f-4cbe-b93c-d632a94b15f6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d615be6270618eb527982656ab228072f24a1a2f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="iconverttypeimpl-class"></a>IConvertTypeImpl 類別
提供的實作[IConvertType](https://msdn.microsoft.com/en-us/library/ms715926.aspx)介面。  
  
## <a name="syntax"></a>語法

```cpp
template <class T>  
class ATL_NO_VTABLE IConvertTypeImpl   
   : public IConvertType, public CConvertHelper  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別，衍生自`IConvertTypeImpl`。  
  
## <a name="members"></a>成員  
  
### <a name="interface-methods"></a>介面方法  
  
|||  
|-|-|  
|[CanConvert](../../data/oledb/iconverttypeimpl-canconvert.md)|命令或上一個資料列集，請提供可用性資訊的型別轉換。|  
  
## <a name="remarks"></a>備註  
 此介面上是強制的命令、 資料列集和索引資料列集。 **IConvertTypeImpl**委派給 OLE DB 所提供的轉換物件，以實作介面。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)
---
title: IConvertTypeImpl 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IConvertTypeImpl<T>
- IConvertTypeImpl
- ATL.IConvertTypeImpl
- ATL::IConvertTypeImpl
- ATL::IConvertTypeImpl<T>
- IConvertTypeImpl.CanConvert
- CanConvert
- IConvertTypeImpl::CanConvert
dev_langs:
- C++
helpviewer_keywords:
- IConvertTypeImpl class
- CanConvert method
ms.assetid: 7f81e79e-7d3f-4cbe-b93c-d632a94b15f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e176cc20dc3f6f13eb868133b99c0ce7e86d25c4
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2018
ms.locfileid: "42572444"
---
# <a name="iconverttypeimpl-class"></a>IConvertTypeImpl 類別
提供實作[IConvertType](/previous-versions/windows/desktop/ms715926\(v=vs.85\))介面。  
  
## <a name="syntax"></a>語法

```cpp
template <class T>  
class ATL_NO_VTABLE IConvertTypeImpl   
   : public IConvertType, public CConvertHelper  
```  
  
### <a name="parameters"></a>參數  
 *T*  
 您的類別，衍生自`IConvertTypeImpl`。  

## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="members"></a>成員  
  
### <a name="interface-methods"></a>介面方法  
  
|||  
|-|-|  
|[CanConvert](#canconvert)|命令或上一個資料列集，請提供可用性資訊的類型轉換。|  
  
## <a name="remarks"></a>備註  
 這個介面是命令、 資料列集和索引資料列集時的必要參數。 `IConvertTypeImpl` 委派給 OLE DB 所提供的轉換物件，以實作介面。  

## <a name="canconvert"></a> Iconverttypeimpl:: Canconvert
命令或上一個資料列集，請提供可用性資訊的類型轉換。  
  
### <a name="syntax"></a>語法  
  
```cpp
STDMETHOD(CanConvert)(DBTYPE wFromType,   
   DBTYPE wToType,   
   DBCONVERTFLAGS dwConvertFlags);  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[IConvertType::CanConvert](/previous-versions/windows/desktop/ms711224\(v=vs.85\))中*OLE DB 程式設計人員參考*。  
  
### <a name="remarks"></a>備註  
 使用中的 OLE DB 資料轉換`MSADC.DLL`。  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)
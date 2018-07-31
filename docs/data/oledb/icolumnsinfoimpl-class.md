---
title: IColumnsInfoImpl 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IColumnsInfoImpl<T>
- ATL::IColumnsInfoImpl
- IColumnsInfoImpl
- ATL.IColumnsInfoImpl
- ATL::IColumnsInfoImpl<T>
- GetColumnInfo
- ATL::IColumnsInfoImpl::GetColumnInfo
- ATL.IColumnsInfoImpl.GetColumnInfo
- ATL::IColumnsInfoImpl<T>::GetColumnInfo
- IColumnsInfoImpl::GetColumnInfo
- IColumnsInfoImpl<T>::GetColumnInfo
- IColumnsInfoImpl.GetColumnInfo
- IColumnsInfoImpl<T>::MapColumnIDs
- MapColumnIDs
- ATL::IColumnsInfoImpl::MapColumnIDs
- IColumnsInfoImpl.MapColumnIDs
- ATL::IColumnsInfoImpl<T>::MapColumnIDs
- IColumnsInfoImpl::MapColumnIDs
- ATL.IColumnsInfoImpl<T>.MapColumnIDs
- ATL.IColumnsInfoImpl.MapColumnIDs
dev_langs:
- C++
helpviewer_keywords:
- IColumnsInfoImpl class
- GetColumnInfo method
- MapColumnIDs method
ms.assetid: ba74c1c5-2eda-4452-8b57-84919fa0d066
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e95ab02abaf4dd536ad6a081708a76cf54cca6b0
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2018
ms.locfileid: "39337238"
---
# <a name="icolumnsinfoimpl-class"></a>IColumnsInfoImpl 類別
提供實作[IColumnsInfo](https://msdn.microsoft.com/library/ms724541.aspx)介面。  
  
## <a name="syntax"></a>語法

```cpp
template <class T>  
class ATL_NO_VTABLE IColumnsInfoImpl :   
   public IColumnsInfo,    
   public CDBIDOps  
```  
  
### <a name="parameters"></a>參數  
 *T*  
 您的類別，衍生自`IColumnsInfoImpl`。  

## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[GetColumnInfo](#getcolumninfo)|傳回大部分消費者所需的資料行中繼資料。|  
|[MapColumnIDs](#mapcolumnids)|在指定的資料行識別碼所識別的資料列集傳回的資料行序數的陣列。|  
  
## <a name="remarks"></a>備註  
 在 資料列集和命令上必要的介面。 若要修改您的提供者的行為`IColumnsInfo`實作中，您需要修改提供者資料行對應。  

## <a name="getcolumninfo"></a> Icolumnsinfoimpl:: Getcolumninfo
傳回大部分消費者所需的資料行中繼資料。  
  
### <a name="syntax"></a>語法  
  
```cpp
STDMETHOD (GetColumnInfo)(DBORDINAL* pcColumns,  
   DBCOLUMNINFO** prgInfo,  
   OLECHAR** ppStringsBuffer);  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[icolumnsinfo:: Getcolumninfo](https://msdn.microsoft.com/library/ms722704.aspx)中*OLE DB 程式設計人員參考*。  

## <a name="mapcolumnids"></a> Icolumnsinfoimpl:: Mapcolumnids
在指定的資料行識別碼所識別的資料列集傳回的資料行序數的陣列。  
  
### <a name="syntax"></a>語法  
  
```cpp
STDMETHOD (MapColumnIDs)(DBORDINAL cColumnIDs,  
   const DBID rgColumnIDs[],  
   DBORDINAL rgColumns[]);  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[IColumnsInfo::MapColumnIDs](https://msdn.microsoft.com/library/ms714200.aspx)中*OLE DB 程式設計人員參考*。  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)
---
title: IConvertTypeImpl 類別
ms.date: 11/04/2016
f1_keywords:
- ATL.IConvertTypeImpl<T>
- IConvertTypeImpl
- ATL.IConvertTypeImpl
- ATL::IConvertTypeImpl
- ATL::IConvertTypeImpl<T>
- IConvertTypeImpl.CanConvert
- CanConvert
- IConvertTypeImpl::CanConvert
helpviewer_keywords:
- IConvertTypeImpl class
- CanConvert method
ms.assetid: 7f81e79e-7d3f-4cbe-b93c-d632a94b15f6
ms.openlocfilehash: 0b3c0f239b3c80d0b4d3c8425b03a3612a0e6db2
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556227"
---
# <a name="iconverttypeimpl-class"></a>IConvertTypeImpl 類別

提供實作[IConvertType](https://docs.microsoft.com/previous-versions/windows/desktop/ms715926(v=vs.85))介面。

## <a name="syntax"></a>語法

```cpp
template <class T>
class ATL_NO_VTABLE IConvertTypeImpl
   : public IConvertType, public CConvertHelper
```

### <a name="parameters"></a>參數

*T*<br/>
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

請參閱[IConvertType::CanConvert](https://docs.microsoft.com/previous-versions/windows/desktop/ms711224(v=vs.85))中*OLE DB 程式設計人員參考*。

### <a name="remarks"></a>備註

使用中的 OLE DB 資料轉換`MSADC.DLL`。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)
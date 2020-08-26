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
ms.openlocfilehash: b4309e794a83e6c13dcf0051791cd1762a6d5012
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845558"
---
# <a name="iconverttypeimpl-class"></a>IConvertTypeImpl 類別

提供 [IConvertType](/previous-versions/windows/desktop/ms715926(v=vs.85)) 介面的實作為。

## <a name="syntax"></a>語法

```cpp
template <class T>
class ATL_NO_VTABLE IConvertTypeImpl
   : public IConvertType, public CConvertHelper
```

### <a name="parameters"></a>參數

*T*<br/>
衍生自的類別 `IConvertTypeImpl` 。

## <a name="requirements"></a>規格需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="interface-methods"></a>介面方法

| 名稱 | 描述 |
|-|-|
|[CanConvert](#canconvert)|提供命令或資料列集上類型轉換的可用性資訊。|

## <a name="remarks"></a>備註

此介面在命令、資料列集和索引資料列集上是必要的。 `IConvertTypeImpl` 藉由委派給 OLE DB 所提供的轉換物件，來實作為介面。

## <a name="iconverttypeimplcanconvert"></a><a name="canconvert"></a> IConvertTypeImpl：： CanConvert

提供命令或資料列集上類型轉換的可用性資訊。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(CanConvert)(DBTYPE wFromType,
   DBTYPE wToType,
   DBCONVERTFLAGS dwConvertFlags);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IConvertType：： CanConvert](/previous-versions/windows/desktop/ms711224(v=vs.85)) 。

### <a name="remarks"></a>備註

使用中 OLE DB 的資料轉換 `MSADC.DLL` 。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)

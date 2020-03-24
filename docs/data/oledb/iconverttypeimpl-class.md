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
ms.openlocfilehash: e3b76be2a1f1edfcdc1139a3dd396835923c2b4a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210687"
---
# <a name="iconverttypeimpl-class"></a>IConvertTypeImpl 類別

提供[IConvertType](/previous-versions/windows/desktop/ms715926(v=vs.85))介面的執行。

## <a name="syntax"></a>語法

```cpp
template <class T>
class ATL_NO_VTABLE IConvertTypeImpl
   : public IConvertType, public CConvertHelper
```

### <a name="parameters"></a>參數

*T*<br/>
衍生自 `IConvertTypeImpl`的類別。

## <a name="requirements"></a>需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="interface-methods"></a>介面方法

|||
|-|-|
|[CanConvert](#canconvert)|提供命令或資料列集上類型轉換可用性的資訊。|

## <a name="remarks"></a>備註

這個介面在命令、資料列集和索引資料列集上是必要的。 `IConvertTypeImpl` 藉由委派給 OLE DB 所提供的轉換物件來執行介面。

## <a name="iconverttypeimplcanconvert"></a><a name="canconvert"></a>IConvertTypeImpl：： CanConvert

提供命令或資料列集上類型轉換可用性的資訊。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(CanConvert)(DBTYPE wFromType,
   DBTYPE wToType,
   DBCONVERTFLAGS dwConvertFlags);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IConvertType：： CanConvert](/previous-versions/windows/desktop/ms711224(v=vs.85)) 。

### <a name="remarks"></a>備註

在 `MSADC.DLL`中使用 OLE DB 的資料轉換。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)

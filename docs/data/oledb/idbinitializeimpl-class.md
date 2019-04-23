---
title: IDBInitializeImpl 類別
ms.date: 11/04/2016
f1_keywords:
- ATL.IDBInitializeImpl<T>
- ATL::IDBInitializeImpl<T>
- IDBInitializeImpl
- ATL::IDBInitializeImpl
- ATL.IDBInitializeImpl
- IDBInitializeImpl.IDBInitializeImpl
- IDBInitializeImpl
- IDBInitializeImpl::IDBInitializeImpl
- Initialize
- IDBInitializeImpl::Initialize
- IDBInitializeImpl.Initialize
- IDBInitializeImpl.Uninitialize
- Uninitialize
- IDBInitializeImpl::Uninitialize
- ATL::IDBInitializeImpl::m_dwStatus
- IDBInitializeImpl.m_dwStatus
- ATL.IDBInitializeImpl.m_dwStatus
- IDBInitializeImpl::m_dwStatus
- IDBInitializeImpl<T>::m_dwStatus
- ATL.IDBInitializeImpl<T>.m_dwStatus
- ATL::IDBInitializeImpl<T>::m_dwStatus
- m_dwStatus
- ATL::IDBInitializeImpl<T>::m_pCUtlPropInfo
- m_pCUtlPropInfo
- IDBInitializeImpl::m_pCUtlPropInfo
- ATL.IDBInitializeImpl.m_pCUtlPropInfo
- IDBInitializeImpl<T>::m_pCUtlPropInfo
- IDBInitializeImpl.m_pCUtlPropInfo
- ATL::IDBInitializeImpl::m_pCUtlPropInfo
helpviewer_keywords:
- IDBInitializeImpl class
- IDBInitializeImpl constructor
- Initialize method
- Uninitialize method
- m_dwStatus
- m_pCUtlPropInfo
ms.assetid: e4182f81-0443-44f5-a0d3-e7e075d6f883
ms.openlocfilehash: 3418ce11e1a607d66fee593b32fd3a4b7d197407
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59033978"
---
# <a name="idbinitializeimpl-class"></a>IDBInitializeImpl 類別

提供實作[IDBInitialize](/previous-versions/windows/desktop/ms713706(v=vs.85))介面。

## <a name="syntax"></a>語法

```cpp
template <class T>
class ATL_NO_VTABLE IDBInitializeImpl : public IDBInitialize
```

### <a name="parameters"></a>參數

*T*<br/>
您的類別，衍生自`IDBInitializeImpl`。

## <a name="requirements"></a>需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[IDBInitializeImpl](#idbinitializeimpl)|建構函式。|

### <a name="interface-methods"></a>介面方法

|||
|-|-|
|[Initialize](#initialize)|啟動提供者。|
|[解除初始化](#uninitialize)|停止提供者。|

### <a name="data-members"></a>資料成員

|||
|-|-|
|[m_dwStatus](#dwstatus)|資料來源的旗標。|
|[m_pCUtlPropInfo](#pcutlpropinfo)|實作 DB 屬性資訊的指標。|

## <a name="remarks"></a>備註

在資料來源物件和選擇性的介面，列舉值的強制介面。

## <a name="idbinitializeimpl"></a> Idbinitializeimpl:: Idbinitializeimpl

建構函式。

### <a name="syntax"></a>語法

```cpp
IDBInitializeImpl();
```

### <a name="remarks"></a>備註

所有資料成員都初始化。

## <a name="initialize"></a> IDBInitializeImpl::Initialize

您可以透過準備資料來源物件的屬性支援來初始化該物件。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(Initialize)(void);
```

### <a name="remarks"></a>備註

請參閱[idbinitialize:: Initialize](/previous-versions/windows/desktop/ms718026(v=vs.85))中*OLE DB 程式設計人員參考*。

## <a name="uninitialize"></a> IDBInitializeImpl::Uninitialize

位置的資料來源物件處於未初始化狀態，釋出內部的資源，例如屬性支援。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(Uninitialize)(void);
```

### <a name="remarks"></a>備註

請參閱[Uninitialize](/previous-versions/windows/desktop/ms719648(v=vs.85))中*OLE DB 程式設計人員參考*。

## <a name="dwstatus"></a> IDBInitializeImpl::m_dwStatus

資料來源的旗標。

### <a name="syntax"></a>語法

```cpp
DWORD m_dwStatus;
```

### <a name="remarks"></a>備註

這些旗標會指定，或指出資料來源物件的各種屬性的狀態。 包含一或多個項目**enum**值：

```cpp
enum DATASOURCE_FLAGS {
    DSF_MASK_INIT     = 0xFFFFF00F,
    DSF_PERSIST_DIRTY = 0x00000001,
    DSF_INITIALIZED   = 0x00000010,
};
```

|||
|-|-|
|`DSF_MASK_INIT`|若要啟用未初始化的狀態還原遮罩。|
|`DSF_PERSIST_DIRTY`|如果資料來源物件 （亦即，如果已有變更），需要持續性，設定。|
|`DSF_INITIALIZED`|如果已初始化資料來源，設定。|

## <a name="pcutlpropinfo"></a> IDBInitializeImpl::m_pCUtlPropInfo

實作物件，如 DB 內容的詳細資訊的指標。

### <a name="syntax"></a>語法

```cpp
CUtlPropInfo< T >* m_pCUtlPropInfo;
```

## <a name="see-also"></a>另請參閱

[OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)
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
ms.openlocfilehash: 511d67586a7adc2b26cc6acbdf39beff78f9c38a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218321"
---
# <a name="idbinitializeimpl-class"></a>IDBInitializeImpl 類別

提供[IDBInitialize](/previous-versions/windows/desktop/ms713706(v=vs.85))介面的執行。

## <a name="syntax"></a>語法

```cpp
template <class T>
class ATL_NO_VTABLE IDBInitializeImpl : public IDBInitialize
```

### <a name="parameters"></a>參數

*T*<br/>
衍生自的類別 `IDBInitializeImpl` 。

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
|[m_dwStatus](#dwstatus)|資料來源旗標。|
|[m_pCUtlPropInfo](#pcutlpropinfo)|資料庫屬性資訊的執行指標。|

## <a name="remarks"></a>備註

資料來源物件上的強制介面和枚舉器上的選擇性介面。

## <a name="idbinitializeimplidbinitializeimpl"></a><a name="idbinitializeimpl"></a>IDBInitializeImpl：： IDBInitializeImpl

建構函式。

### <a name="syntax"></a>語法

```cpp
IDBInitializeImpl();
```

### <a name="remarks"></a>備註

初始化所有資料成員。

## <a name="idbinitializeimplinitialize"></a><a name="initialize"></a>IDBInitializeImpl：： Initialize

您可以透過準備資料來源物件的屬性支援來初始化該物件。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(Initialize)(void);
```

### <a name="remarks"></a>備註

請參閱 OLE DB 程式設計*人員參考*中的[IDBInitialize：： Initialize](/previous-versions/windows/desktop/ms718026(v=vs.85)) 。

## <a name="idbinitializeimpluninitialize"></a><a name="uninitialize"></a>IDBInitializeImpl：：解除初始化

藉由釋放內部資源（例如屬性支援），將資料來源物件置於未初始化的狀態。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(Uninitialize)(void);
```

### <a name="remarks"></a>備註

請參閱 OLE DB 程式設計*人員參考*中的[IDBInitialize：：解除初始化](/previous-versions/windows/desktop/ms719648(v=vs.85))。

## <a name="idbinitializeimplm_dwstatus"></a><a name="dwstatus"></a>IDBInitializeImpl：： m_dwStatus

資料來源旗標。

### <a name="syntax"></a>語法

```cpp
DWORD m_dwStatus;
```

### <a name="remarks"></a>備註

這些旗標會指定或指出資料來源物件之各種屬性的狀態。 包含下列一個或多個 **`enum`** 值：

```cpp
enum DATASOURCE_FLAGS {
    DSF_MASK_INIT     = 0xFFFFF00F,
    DSF_PERSIST_DIRTY = 0x00000001,
    DSF_INITIALIZED   = 0x00000010,
};
```

|||
|-|-|
|`DSF_MASK_INIT`|遮罩，可啟用未初始化狀態的還原。|
|`DSF_PERSIST_DIRTY`|設定資料來源物件是否需要持續性（也就是，如果有變更的話）。|
|`DSF_INITIALIZED`|設定資料來源是否已初始化。|

## <a name="idbinitializeimplm_pcutlpropinfo"></a><a name="pcutlpropinfo"></a>IDBInitializeImpl：： m_pCUtlPropInfo

DB 屬性資訊的執行物件指標。

### <a name="syntax"></a>語法

```cpp
CUtlPropInfo< T >* m_pCUtlPropInfo;
```

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)

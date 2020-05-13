---
title: IRunn 可物件 Implclass
ms.date: 11/04/2016
f1_keywords:
- IRunnableObjectImpl
- ATLCTL/ATL::IRunnableObjectImpl
- ATLCTL/ATL::IRunnableObjectImpl::GetRunningClass
- ATLCTL/ATL::IRunnableObjectImpl::IsRunning
- ATLCTL/ATL::IRunnableObjectImpl::LockRunning
- ATLCTL/ATL::IRunnableObjectImpl::Run
- ATLCTL/ATL::IRunnableObjectImpl::SetContainedObject
helpviewer_keywords:
- containers, running controls
- IRunnableObjectImpl class
- IRunnableObject, ATL implementation
- controls [ATL], running
- controls [C++], container running in ATL
ms.assetid: 305c7c3b-889e-49dd-aca1-34379c1b9931
ms.openlocfilehash: 2843c0c25a5c104ffbdff72255ac5d85cf53b1ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329451"
---
# <a name="irunnableobjectimpl-class"></a>IRunn 可物件 Implclass

此類實現`IUnknown`並提供[IRunnableObject 介面](/windows/win32/api/objidl/nn-objidl-irunnableobject)的預設實現。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template<class T>
class IRunnableObjectImpl
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類,派生自`IRunnableObjectImpl`。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IRunn 可物件Impl::取得運行類](#getrunningclass)|返回正在運行的控制件的 CLSID。 ATL 實現將 CLSID 設置為GUID_NULL並返回E_UNEXPECTED。|
|[執行物件impl::正在執行](#isrunning)|確定控件是否正在運行。 ATL 實現返回 TRUE。|
|[執行物件Impl::鎖定執行](#lockrunning)|將控制器鎖定到運行狀態。 ATL 實現返回S_OK。|
|[IRunnable 物件Impl::執行](#run)|強制控件運行。 ATL 實現返回S_OK。|
|[執行物件 Impl::設定包含物件](#setcontainedobject)|指示控件已嵌入。 ATL 實現返回S_OK。|

## <a name="remarks"></a>備註

[IRunnableObject](/windows/win32/api/objidl/nn-objidl-irunnableobject)介面使容器能夠確定控制項是否正在執行、強制它執行或將其鎖定到運行狀態。 類`IRunnableObjectImpl`通過在調試生成中向轉儲設備`IUnknown`發送 資訊來提供此介面的默認實現和實現。

**相關文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md), 建立[ATL 專案](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IRunnableObject`

`IRunnableObjectImpl`

## <a name="requirements"></a>需求

**標題:** atlctl.h

## <a name="irunnableobjectimplgetrunningclass"></a><a name="getrunningclass"></a>IRunn 可物件Impl::取得運行類

返回正在運行的控制件的 CLSID。

```
HRESULT GetRunningClass(LPCLSID lpClsid);
```

### <a name="return-value"></a>傳回值

ATL 實現\*將*lpClsid*集到GUID_NULL並返回E_UNEXPECTED。

### <a name="remarks"></a>備註

請參閱[IRunnableObject:獲取](/windows/win32/api/objidl/nf-objidl-irunnableobject-getrunningclass)Windows SDK 中的運行類。

## <a name="irunnableobjectimplisrunning"></a><a name="isrunning"></a>執行物件impl::正在執行

確定控件是否正在運行。

```
virtual BOOL IsRunning();
```

### <a name="return-value"></a>傳回值

ATL 實現返回 TRUE。

### <a name="remarks"></a>備註

請參閱[IRunnableObject:正在](/windows/win32/api/objidl/nf-objidl-irunnableobject-isrunning)Windows SDK 中執行。

## <a name="irunnableobjectimpllockrunning"></a><a name="lockrunning"></a>執行物件Impl::鎖定執行

將控制器鎖定到運行狀態。

```
HRESULT LockRunning(BOOL fLock, BOOL fLastUnlockCloses);
```

### <a name="return-value"></a>傳回值

ATL 實現返回S_OK。

### <a name="remarks"></a>備註

請參閱[IRunnableObject::在](/windows/win32/api/objidl/nf-objidl-irunnableobject-lockrunning)Windows SDK 中鎖定運行。

## <a name="irunnableobjectimplrun"></a><a name="run"></a>IRunnable 物件Impl::執行

強制控件運行。

```
HRESULT Run(LPBINDCTX lpbc);
```

### <a name="return-value"></a>傳回值

ATL 實現返回S_OK。

### <a name="remarks"></a>備註

請參閱[IRunnableObject::](/windows/win32/api/objidl/nf-objidl-irunnableobject-run)在 Windows SDK 中執行。

## <a name="irunnableobjectimplsetcontainedobject"></a><a name="setcontainedobject"></a>執行物件 Impl::設定包含物件

指示控件已嵌入。

```
HRESULT SetContainedObject(BOOL fContained);
```

### <a name="return-value"></a>傳回值

ATL 實現返回S_OK。

### <a name="remarks"></a>備註

請參閱[IRunnableObject::在](/windows/win32/api/objidl/nf-objidl-irunnableobject-setcontainedobject)Windows SDK 中設置包含物件。

## <a name="see-also"></a>另請參閱

[CComControl 類別](../../atl/reference/ccomcontrol-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)

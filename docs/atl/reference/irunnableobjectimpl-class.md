---
title: IRunnableObjectImpl 類別
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
ms.openlocfilehash: 6b1af7c21c6f5028ad6d3a228cb22650fa3cef42
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495674"
---
# <a name="irunnableobjectimpl-class"></a>IRunnableObjectImpl 類別

這個類別`IUnknown`會執行並提供[IRunnableObject](/windows/win32/api/objidl/nn-objidl-irunnableobject)介面的預設實值。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template<class T>
class IRunnableObjectImpl
```

#### <a name="parameters"></a>參數

*T*<br/>
衍生自`IRunnableObjectImpl`的類別。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IRunnableObjectImpl::GetRunningClass](#getrunningclass)|傳回執行中控制項的 CLSID。 ATL 執行會將 CLSID 設定為 GUID_Null, 並傳回 E_UNEXPECTED。|
|[IRunnableObjectImpl::IsRunning](#isrunning)|判斷控制項是否正在執行。 ATL 實值會傳回 TRUE。|
|[IRunnableObjectImpl::LockRunning](#lockrunning)|將控制項鎖定為執行中狀態。 ATL 實作為傳回 S_OK。|
|[IRunnableObjectImpl::Run](#run)|強制執行控制項。 ATL 實作為傳回 S_OK。|
|[IRunnableObjectImpl::SetContainedObject](#setcontainedobject)|表示控制項是內嵌的。 ATL 實作為傳回 S_OK。|

## <a name="remarks"></a>備註

[IRunnableObject](/windows/win32/api/objidl/nn-objidl-irunnableobject)介面可讓容器判斷某個控制項是否正在執行、強制執行, 或將它鎖定為執行中狀態。 類別`IRunnableObjectImpl`提供此介面的預設執行, 並藉`IUnknown`由將資訊傳送至偵錯工具組建中的傾印裝置來實現。

**相關文章**[Atl 教學](../../atl/active-template-library-atl-tutorial.md)課程,[建立 atl 專案](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>繼承階層

`IRunnableObject`

`IRunnableObjectImpl`

## <a name="requirements"></a>需求

**標頭:** atlctl。h

##  <a name="getrunningclass"></a>IRunnableObjectImpl::GetRunningClass

傳回執行中控制項的 CLSID。

```
HRESULT GetRunningClass(LPCLSID lpClsid);
```

### <a name="return-value"></a>傳回值

ATL 執行會將\* *lpClsid*設定為 GUID_Null, 並傳回 E_UNEXPECTED。

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IRunnableObject:: GetRunningClass](/windows/win32/api/objidl/nf-objidl-irunnableobject-getrunningclass) 。

##  <a name="isrunning"></a>IRunnableObjectImpl:: IsRunning

判斷控制項是否正在執行。

```
virtual BOOL IsRunning();
```

### <a name="return-value"></a>傳回值

ATL 實值會傳回 TRUE。

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IRunnableObject:: IsRunning](/windows/win32/api/objidl/nf-objidl-irunnableobject-isrunning) 。

##  <a name="lockrunning"></a>IRunnableObjectImpl::LockRunning

將控制項鎖定為執行中狀態。

```
HRESULT LockRunning(BOOL fLock, BOOL fLastUnlockCloses);
```

### <a name="return-value"></a>傳回值

ATL 實作為傳回 S_OK。

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IRunnableObject:: LockRunning](/windows/win32/api/objidl/nf-objidl-irunnableobject-lockrunning) 。

##  <a name="run"></a>IRunnableObjectImpl:: Run

強制執行控制項。

```
HRESULT Run(LPBINDCTX lpbc);
```

### <a name="return-value"></a>傳回值

ATL 實作為傳回 S_OK。

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IRunnableObject:: Run](/windows/win32/api/objidl/nf-objidl-irunnableobject-run) 。

##  <a name="setcontainedobject"></a>  IRunnableObjectImpl::SetContainedObject

表示控制項是內嵌的。

```
HRESULT SetContainedObject(BOOL fContained);
```

### <a name="return-value"></a>傳回值

ATL 實作為傳回 S_OK。

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IRunnableObject:: SetContainedObject](/windows/win32/api/objidl/nf-objidl-irunnableobject-setcontainedobject) 。

## <a name="see-also"></a>另請參閱

[CComControl 類別](../../atl/reference/ccomcontrol-class.md)<br/>
[類別總覽](../../atl/atl-class-overview.md)

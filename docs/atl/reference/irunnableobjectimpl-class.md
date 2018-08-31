---
title: IRunnableObjectImpl 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IRunnableObjectImpl
- ATLCTL/ATL::IRunnableObjectImpl
- ATLCTL/ATL::IRunnableObjectImpl::GetRunningClass
- ATLCTL/ATL::IRunnableObjectImpl::IsRunning
- ATLCTL/ATL::IRunnableObjectImpl::LockRunning
- ATLCTL/ATL::IRunnableObjectImpl::Run
- ATLCTL/ATL::IRunnableObjectImpl::SetContainedObject
dev_langs:
- C++
helpviewer_keywords:
- containers, running controls
- IRunnableObjectImpl class
- IRunnableObject, ATL implementation
- controls [ATL], running
- controls [C++], container running in ATL
ms.assetid: 305c7c3b-889e-49dd-aca1-34379c1b9931
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 035d59d71dc7166b12b6e894803645aacda83887
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43218694"
---
# <a name="irunnableobjectimpl-class"></a>IRunnableObjectImpl 類別
這個類別會實作`IUnknown`，並提供的預設實作[IRunnableObject](/windows/desktop/api/objidl/nn-objidl-irunnableobject)介面。  
  
> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template<class T>  
class IRunnableObjectImpl
```  
  
#### <a name="parameters"></a>參數  
 *T*  
 您的類別，衍生自`IRunnableObjectImpl`。  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[IRunnableObjectImpl::GetRunningClass](#getrunningclass)|傳回執行控制項的 CLSID。 ATL 實作設 GUID_NULL 的 CLSID，並傳回 E_UNEXPECTED。|  
|[IRunnableObjectImpl::IsRunning](#isrunning)|判斷控制項是否正在執行。 ATL 實作會傳回 TRUE。|  
|[IRunnableObjectImpl::LockRunning](#lockrunning)|鎖定控制項進入執行狀態。 ATL 實作會傳回 S_OK。|  
|[IRunnableObjectImpl::Run](#run)|強制執行控制項。 ATL 實作會傳回 S_OK。|  
|[IRunnableObjectImpl::SetContainedObject](#setcontainedobject)|表示控制項內嵌。 ATL 實作會傳回 S_OK。|  
  
## <a name="remarks"></a>備註  
 [IRunnableObject](/windows/desktop/api/objidl/nn-objidl-irunnableobject)介面可讓容器，以判斷控制項是否正在執行，強制執行，或鎖定進入執行狀態。 類別`IRunnableObjectImpl`提供此介面的預設實作，並實作`IUnknown`資訊傳送給傾印裝置在偵錯組建。  
  
 **相關文章** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)，[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IRunnableObject`  
  
 `IRunnableObjectImpl`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlctl.h  
  
##  <a name="getrunningclass"></a>  IRunnableObjectImpl::GetRunningClass  
 傳回執行控制項的 CLSID。  
  
```
HRESULT GetRunningClass(LPCLSID lpClsid);
```  
  
### <a name="return-value"></a>傳回值  
 ATL 實作集合\* *lpClsid* GUID_NULL，然後傳回 E_UNEXPECTED。  
  
### <a name="remarks"></a>備註  
 請參閱[IRunnableObject::GetRunningClass](/windows/desktop/api/objidl/nf-objidl-irunnableobject-getrunningclass) Windows SDK 中。  
  
##  <a name="isrunning"></a>  IRunnableObjectImpl::IsRunning  
 判斷控制項是否正在執行。  
  
```
virtual BOOL IsRunning();
```  
  
### <a name="return-value"></a>傳回值  
 ATL 實作會傳回 TRUE。  
  
### <a name="remarks"></a>備註  
 請參閱[IRunnableObject::IsRunning](/windows/desktop/api/objidl/nf-objidl-irunnableobject-isrunning) Windows SDK 中。  
  
##  <a name="lockrunning"></a>  IRunnableObjectImpl::LockRunning  
 鎖定控制項進入執行狀態。  
  
```
HRESULT LockRunning(BOOL fLock, BOOL fLastUnlockCloses);
```  
  
### <a name="return-value"></a>傳回值  
 ATL 實作會傳回 S_OK。  
  
### <a name="remarks"></a>備註  
 請參閱[IRunnableObject::LockRunning](/windows/desktop/api/objidl/nf-objidl-irunnableobject-lockrunning) Windows SDK 中。  
  
##  <a name="run"></a>  IRunnableObjectImpl::Run  
 強制執行控制項。  
  
```
HRESULT Run(LPBINDCTX lpbc);
```  
  
### <a name="return-value"></a>傳回值  
 ATL 實作會傳回 S_OK。  
  
### <a name="remarks"></a>備註  
 請參閱[IRunnableObject::Run](/windows/desktop/api/objidl/nf-objidl-irunnableobject-run) Windows SDK 中。  
  
##  <a name="setcontainedobject"></a>  IRunnableObjectImpl::SetContainedObject  
 表示控制項內嵌。  
  
```
HRESULT SetContainedObject(BOOL fContained);
```  
  
### <a name="return-value"></a>傳回值  
 ATL 實作會傳回 S_OK。  
  
### <a name="remarks"></a>備註  
 請參閱[IRunnableObject::SetContainedObject](/windows/desktop/api/objidl/nf-objidl-irunnableobject-setcontainedobject) Windows SDK 中。  
  
## <a name="see-also"></a>另請參閱  
 [CComControl 類別](../../atl/reference/ccomcontrol-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

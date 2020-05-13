---
title: CD2DResource 類別
ms.date: 03/27/2019
f1_keywords:
- CD2DResource
- AFXRENDERTARGET/CD2DResource
- AFXRENDERTARGET/CD2DResource::CD2DResource
- AFXRENDERTARGET/CD2DResource::Create
- AFXRENDERTARGET/CD2DResource::Destroy
- AFXRENDERTARGET/CD2DResource::IsValid
- AFXRENDERTARGET/CD2DResource::IsAutoDestroy
- AFXRENDERTARGET/CD2DResource::ReCreate
- AFXRENDERTARGET/CD2DResource::m_bIsAutoDestroy
- AFXRENDERTARGET/CD2DResource::m_pParentTarget
helpviewer_keywords:
- CD2DResource [MFC], CD2DResource
- CD2DResource [MFC], Create
- CD2DResource [MFC], Destroy
- CD2DResource [MFC], IsValid
- CD2DResource [MFC], IsAutoDestroy
- CD2DResource [MFC], ReCreate
- CD2DResource [MFC], m_bIsAutoDestroy
- CD2DResource [MFC], m_pParentTarget
ms.assetid: 34e3ee18-aab6-4c39-9294-de869e1f7820
ms.openlocfilehash: 5e747eda42e625d0f4cf65859e471933bbb043ed
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369100"
---
# <a name="cd2dresource-class"></a>CD2DResource 類別

提供用於創建和管理 D2D 資源(如畫筆、圖層和文本)的介面的抽象類。

## <a name="syntax"></a>語法

```
class CD2DResource : public CObject;
```

## <a name="members"></a>成員

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|描述|
|----------|-----------------|
|[CD2D 資源:CD2D 資源](#cd2dresource)|建構 CD2D 資源物件。|
|[CD2D 資源:*CD2D 資源](#_dtorcd2dresource)|解構函式。 銷毀 D2D 資源物件時調用。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CD2D 資源:建立](#create)|創建 CD2D 資源。|
|[CD2D資源::D](#destroy)|銷毀 CD2D 資源物件。|
|[CD2D 資源:有效](#isvalid)|檢查資源有效性|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CD2D 資源::自動銷毀](#isautodestroy)|檢查自動銷毀標誌。|
|[CD2D 資源:重新建立](#recreate)|重新建立 CD2D 資源。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CD2D 資源:m_bIsAutoDestroy](#m_bisautodestroy)|資源將被擁有者銷毀 (CRenderTarget)|
|[CD2D 資源:m_pParentTarget](#m_pparenttarget)|指向父 CRenderTarget 的指標)|

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CD2DResource`

## <a name="requirements"></a>需求

**標題:** afxrendertarget.h

## <a name="cd2dresourcecd2dresource"></a><a name="_dtorcd2dresource"></a>CD2D 資源:*CD2D 資源

解構函式。 銷毀 D2D 資源物件時調用。

```
virtual ~CD2DResource();
```

## <a name="cd2dresourcecd2dresource"></a><a name="cd2dresource"></a>CD2D 資源:CD2D 資源

建構 CD2D 資源物件。

```
CD2DResource(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy);
```

### <a name="parameters"></a>參數

*p 父目標*<br/>
指向渲染目標的指標。

*bAuto銷毀*<br/>
指示物件將被擁有者(pParentTarget)銷毀。

## <a name="cd2dresourcecreate"></a><a name="create"></a>CD2D 資源:建立

創建 CD2D 資源。

```
virtual HRESULT Create(CRenderTarget* pRenderTarget) = 0;
```

### <a name="parameters"></a>參數

*pRender 目標*<br/>
指向渲染目標的指標。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 S_OK。 否則,它將返回一個HRESULT錯誤代碼。

## <a name="cd2dresourcedestroy"></a><a name="destroy"></a>CD2D資源::D

銷毀 CD2D 資源物件。

```
virtual void Destroy() = 0;
```

## <a name="cd2dresourceisautodestroy"></a><a name="isautodestroy"></a>CD2D 資源::自動銷毀

檢查自動銷毀標誌。

```
BOOL IsAutoDestroy() const;
```

### <a name="return-value"></a>傳回值

如果物件將被其擁有者銷毀,則為 TRUE;否則 FALSE。

## <a name="cd2dresourceisvalid"></a><a name="isvalid"></a>CD2D 資源:有效

檢查資源有效性

```
virtual BOOL IsValid() const = 0;
```

### <a name="return-value"></a>傳回值

如果資源有效,則為 TRUE;否則 FALSE。

## <a name="cd2dresourcem_bisautodestroy"></a><a name="m_bisautodestroy"></a>CD2D 資源:m_bIsAutoDestroy

資源將被擁有者銷毀 (CRenderTarget)

```
BOOL m_bIsAutoDestroy;
```

## <a name="cd2dresourcem_pparenttarget"></a><a name="m_pparenttarget"></a>CD2D 資源:m_pParentTarget

指向父 CRenderTarget 的指標)

```
CRenderTarget* m_pParentTarget;
```

## <a name="cd2dresourcerecreate"></a><a name="recreate"></a>CD2D 資源:重新建立

重新建立 CD2D 資源。

```
virtual HRESULT ReCreate(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>參數

*pRender 目標*<br/>
指向渲染目標的指標。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 S_OK。 否則,它將返回一個HRESULT錯誤代碼。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)

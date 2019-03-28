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
ms.openlocfilehash: e2cc6be7119a2df193aa2af415a9c8d4054f537c
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2019
ms.locfileid: "58564771"
---
# <a name="cd2dresource-class"></a>CD2DResource 類別

抽象類別，提供用於建立和管理 D2D 資源，例如筆刷、 圖層，以及文字的介面。

## <a name="syntax"></a>語法

```
class CD2DResource : public CObject;
```

## <a name="members"></a>成員

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|描述|
|----------|-----------------|
|[CD2DResource::CD2DResource](#cd2dresource)|建構 CD2DResource 物件。|
|[CD2DResource::~CD2DResource](#_dtorcd2dresource)|解構函式。 D2D 資源物件正在被終結時呼叫。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CD2DResource::Create](#create)|建立 CD2DResource。|
|[CD2DResource::Destroy](#destroy)|終結 CD2DResource 物件。|
|[CD2DResource::IsValid](#isvalid)|檢查資源的有效性|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CD2DResource::IsAutoDestroy](#isautodestroy)|核取自動終結旗標。|
|[CD2DResource::ReCreate](#recreate)|CD2DResource 會重新建立。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CD2DResource::m_bIsAutoDestroy](#m_bisautodestroy)|資源將被終結擁有者 (CRenderTarget)|
|[CD2DResource::m_pParentTarget](#m_pparenttarget)|父 CRenderTarget 指標）|

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CD2DResource`

## <a name="requirements"></a>需求

**標頭：** afxrendertarget.h

##  <a name="_dtorcd2dresource"></a>  CD2DResource:: ~ CD2DResource

解構函式。 D2D 資源物件正在被終結時呼叫。

```
virtual ~CD2DResource();
```

##  <a name="cd2dresource"></a>  CD2DResource::CD2DResource

建構 CD2DResource 物件。

```
CD2DResource(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy);
```

### <a name="parameters"></a>參數

*pParentTarget*<br/>
到轉譯目標的指標。

*bAutoDestroy*<br/>
表示擁有者 (pParentTarget) 將會終結物件。

##  <a name="create"></a>  CD2DResource::Create

建立 CD2DResource。

```
virtual HRESULT Create(CRenderTarget* pRenderTarget) = 0;
```

### <a name="parameters"></a>參數

*pRenderTarget*<br/>
到轉譯目標的指標。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 S_OK。 否則，它會傳回 HRESULT 錯誤碼。

##  <a name="destroy"></a>  CD2DResource::Destroy

終結 CD2DResource 物件。

```
virtual void Destroy() = 0;
```

##  <a name="isautodestroy"></a>  CD2DResource::IsAutoDestroy

核取自動終結旗標。

```
BOOL IsAutoDestroy() const;
```

### <a name="return-value"></a>傳回值

如果將終結物件，由其擁有者，則為 TRUE否則為 FALSE。

##  <a name="isvalid"></a>  CD2DResource::IsValid

檢查資源的有效性

```
virtual BOOL IsValid() const = 0;
```

### <a name="return-value"></a>傳回值

如果資源無效，則為 TRUE否則為 FALSE。

##  <a name="m_bisautodestroy"></a>  CD2DResource::m_bIsAutoDestroy

資源將被終結擁有者 (CRenderTarget)

```
BOOL m_bIsAutoDestroy;
```

##  <a name="m_pparenttarget"></a>  CD2DResource::m_pParentTarget

父 CRenderTarget 指標）

```
CRenderTarget* m_pParentTarget;
```

##  <a name="recreate"></a>  CD2DResource::ReCreate

CD2DResource 會重新建立。

```
virtual HRESULT ReCreate(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>參數

*pRenderTarget*<br/>
到轉譯目標的指標。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 S_OK。 否則，它會傳回 HRESULT 錯誤碼。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)

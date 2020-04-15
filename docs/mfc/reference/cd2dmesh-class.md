---
title: CD2DMesh 類別
ms.date: 11/04/2016
f1_keywords:
- CD2DMesh
- AFXRENDERTARGET/CD2DMesh
- AFXRENDERTARGET/CD2DMesh::CD2DMesh
- AFXRENDERTARGET/CD2DMesh::Attach
- AFXRENDERTARGET/CD2DMesh::Create
- AFXRENDERTARGET/CD2DMesh::Destroy
- AFXRENDERTARGET/CD2DMesh::Detach
- AFXRENDERTARGET/CD2DMesh::Get
- AFXRENDERTARGET/CD2DMesh::IsValid
- AFXRENDERTARGET/CD2DMesh::Open
- AFXRENDERTARGET/CD2DMesh::m_pMesh
helpviewer_keywords:
- CD2DMesh [MFC], CD2DMesh
- CD2DMesh [MFC], Attach
- CD2DMesh [MFC], Create
- CD2DMesh [MFC], Destroy
- CD2DMesh [MFC], Detach
- CD2DMesh [MFC], Get
- CD2DMesh [MFC], IsValid
- CD2DMesh [MFC], Open
- CD2DMesh [MFC], m_pMesh
ms.assetid: 11a2c78a-1367-40e8-a34f-44aa0509a4c9
ms.openlocfilehash: 64f5dd7b40853a86dc7f964ecd3701f132a94e16
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369187"
---
# <a name="cd2dmesh-class"></a>CD2DMesh 類別

ID2D1Mesh 的包裝器。

## <a name="syntax"></a>語法

```
class CD2DMesh : public CD2DResource;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CD2D 網線:CD2D網格](#cd2dmesh)|構造 CD2DMesh 物件。|
|[CD2D 網線:*CD2D網格](#_dtorcd2dmesh)|解構函式。 銷毀 D2D 網格物件時調用。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CD2D 網線:附加](#attach)|將現有資源介面附加到物件|
|[CD2D 網線:建立](#create)|建立 CD2D 網格。 (覆寫[CD2D 資源:建立](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DMesh::D](#destroy)|銷毀 CD2DMesh 物件。 (覆蓋[CD2D 資源::D)](../../mfc/reference/cd2dresource-class.md#destroy)|
|[CD2DMesh::D埃塔奇](#detach)|從物件分離資源介面|
|[CD2D 網格:取得](#get)|傳回 ID2D1Mesh 介面|
|[CD2DMesh:有效](#isvalid)|檢查資源有效性(覆寫[CD2D 資源::有效](../../mfc/reference/cd2dresource-class.md#isvalid)。)|
|[CD2D 網線::開啟](#open)|打開網格以表示總體。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CD2D 網格::操作員 ID2D1Mesh*](#operator_id2d1mesh_star)|傳回 ID2D1Mesh 介面|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CD2DMesh:m_pMesh](#m_pmesh)|指向 ID2D1Mesh 的指標。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CD2D 資源](../../mfc/reference/cd2dresource-class.md)

`CD2DMesh`

## <a name="requirements"></a>需求

**標題:** afxrendertarget.h

## <a name="cd2dmeshcd2dmesh"></a><a name="_dtorcd2dmesh"></a>CD2D 網線:*CD2D網格

解構函式。 銷毀 D2D 網格物件時調用。

```
virtual ~CD2DMesh();
```

## <a name="cd2dmeshattach"></a><a name="attach"></a>CD2D 網線:附加

將現有資源介面附加到物件

```
void Attach(ID2D1Mesh* pResource);
```

### <a name="parameters"></a>參數

*p資源*<br/>
現有資源介面。 無法為 NULL

## <a name="cd2dmeshcd2dmesh"></a><a name="cd2dmesh"></a>CD2D 網線:CD2D網格

構造 CD2DMesh 物件。

```
CD2DMesh(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>參數

*p 父目標*<br/>
指向渲染目標的指標。

*bAuto銷毀*<br/>
指示物件將被擁有者(pParentTarget)銷毀。

## <a name="cd2dmeshcreate"></a><a name="create"></a>CD2D 網線:建立

建立 CD2D 網格。

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>參數

*pRender 目標*<br/>
指向渲染目標的指標。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 S_OK。 否則,它將返回一個HRESULT錯誤代碼。

## <a name="cd2dmeshdestroy"></a><a name="destroy"></a>CD2DMesh::D

銷毀 CD2DMesh 物件。

```
virtual void Destroy();
```

## <a name="cd2dmeshdetach"></a><a name="detach"></a>CD2DMesh::D埃塔奇

從物件分離資源介面

```
ID2D1Mesh* Detach();
```

### <a name="return-value"></a>傳回值

指向分離的資源介面的指標。

## <a name="cd2dmeshget"></a><a name="get"></a>CD2D 網格:取得

傳回 ID2D1Mesh 介面

```
ID2D1Mesh* Get();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化,則指向 ID2D1Mesh 介面或 NULL 的指標。

## <a name="cd2dmeshisvalid"></a><a name="isvalid"></a>CD2DMesh:有效

檢查資源有效性

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>傳回值

如果資源有效,則為 TRUE;否則 FALSE。

## <a name="cd2dmeshm_pmesh"></a><a name="m_pmesh"></a>CD2DMesh:m_pMesh

指向 ID2D1Mesh 的指標。

```
ID2D1Mesh* m_pMesh;
```

## <a name="cd2dmeshopen"></a><a name="open"></a>CD2D 網線::開啟

打開網格以表示總體。

```
ID2D1TessellationSink* Open();
```

### <a name="return-value"></a>傳回值

指向用於填充網格的 ID2D1Tesssssink 的指標。

## <a name="cd2dmeshoperator-id2d1mesh"></a><a name="operator_id2d1mesh_star"></a>CD2D 網格::操作員 ID2D1Mesh*

傳回 ID2D1Mesh 介面

```
operator ID2D1Mesh*();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化,則指向 ID2D1Mesh 介面或 NULL 的指標。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)

---
title: CDCRenderTarget 類別
ms.date: 11/04/2016
f1_keywords:
- CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::Attach
- AFXRENDERTARGET/CDCRenderTarget::BindDC
- AFXRENDERTARGET/CDCRenderTarget::Create
- AFXRENDERTARGET/CDCRenderTarget::Detach
- AFXRENDERTARGET/CDCRenderTarget::GetDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::m_pDCRenderTarget
helpviewer_keywords:
- CDCRenderTarget [MFC], CDCRenderTarget
- CDCRenderTarget [MFC], Attach
- CDCRenderTarget [MFC], BindDC
- CDCRenderTarget [MFC], Create
- CDCRenderTarget [MFC], Detach
- CDCRenderTarget [MFC], GetDCRenderTarget
- CDCRenderTarget [MFC], m_pDCRenderTarget
ms.assetid: aa8059c9-08e6-49e4-9b8c-00fa54077a61
ms.openlocfilehash: 790ce0f32c2325fa0ea92ca0bda64ddaa4c86c45
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375698"
---
# <a name="cdcrendertarget-class"></a>CDCRenderTarget 類別

ID2D1DCRenderTarget 的包裝器。

## <a name="syntax"></a>語法

```
class CDCRenderTarget : public CRenderTarget;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CDC 渲染目標::CDC 呈現目標](#cdcrendertarget)|構造 CDCRenderTarget 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDC 呈現目標::附加](#attach)|將現有渲染目標介面附加到物件|
|[CDC 呈現目標::結合DC](#binddc)|將成成目標連結為發出繪製指令的裝置上下文|
|[CDC 呈現目標:建立](#create)|創建 CDCRenderTarget。|
|[CDC 渲染目標::D](#detach)|從物件分離成成目標介面|
|[CDC 渲染目標::取得DCRender目標](#getdcrendertarget)|傳回 ID2D1DCRenderTarget 介面|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CDC 渲染目標::操作員 ID2D1DCRenderTarget*](#operator_id2d1dcrendertarget_star)|傳回 ID2D1DCRenderTarget 介面|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CDC 呈現目標::m_pDCRenderTarget](#m_pdcrendertarget)|指向 ID2D1DCRenderTarget 物件的指標。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CRender 目標](../../mfc/reference/crendertarget-class.md)

[CDC 渲染目標](../../mfc/reference/cdcrendertarget-class.md)

## <a name="requirements"></a>需求

**標題:** afxrendertarget.h

## <a name="cdcrendertargetattach"></a><a name="attach"></a>CDC 呈現目標::附加

將現有渲染目標介面附加到物件

```
void Attach(ID2D1DCRenderTarget* pTarget);
```

### <a name="parameters"></a>參數

*p 目標*<br/>
現有渲染目標介面。 無法為 NULL

## <a name="cdcrendertargetbinddc"></a><a name="binddc"></a>CDC 呈現目標::結合DC

將成成目標連結為發出繪製指令的裝置上下文

```
BOOL BindDC(
    const CDC& dc,
    const CRect& rect);
```

### <a name="parameters"></a>參數

*直流*<br/>
顯示目標發出繪製指令的裝置上下文

*矩形*<br/>
呈現目標繫結到的裝置上下文 (HDC) 的句柄的尺寸

### <a name="return-value"></a>傳回值

如果該方法成功,它將返回 TRUE。 否則,它將返回 FALSE。

## <a name="cdcrendertargetcdcrendertarget"></a><a name="cdcrendertarget"></a>CDC 渲染目標::CDC 呈現目標

構造 CDCRenderTarget 物件。

```
CDCRenderTarget();
```

## <a name="cdcrendertargetcreate"></a><a name="create"></a>CDC 呈現目標:建立

創建 CDCRenderTarget。

```
BOOL Create(const D2D1_RENDER_TARGET_PROPERTIES& props);
```

### <a name="parameters"></a>參數

*道具*<br/>
渲染模式、圖元格式、遠端處理選項、DPI 資訊以及硬體渲染所需的最小 DirectX 支援。

### <a name="return-value"></a>傳回值

如果該方法成功,它將返回 TRUE。 否則,它將返回 FALSE。

## <a name="cdcrendertargetdetach"></a><a name="detach"></a>CDC 渲染目標::D

從物件分離成成目標介面

```
ID2D1DCRenderTarget* Detach();
```

### <a name="return-value"></a>傳回值

指向分離的渲染目標介面的指標。

## <a name="cdcrendertargetgetdcrendertarget"></a><a name="getdcrendertarget"></a>CDC 渲染目標::取得DCRender目標

傳回 ID2D1DCRenderTarget 介面

```
ID2D1DCRenderTarget* GetDCRenderTarget();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化,則指向 ID2D1DCRenderTarget 介面或 NULL 的指標。

## <a name="cdcrendertargetm_pdcrendertarget"></a><a name="m_pdcrendertarget"></a>CDC 呈現目標::m_pDCRenderTarget

指向 ID2D1DCRenderTarget 物件的指標。

```
ID2D1DCRenderTarget* m_pDCRenderTarget;
```

## <a name="cdcrendertargetoperator-id2d1dcrendertarget"></a><a name="operator_id2d1dcrendertarget_star"></a>CDC 渲染目標::操作員 ID2D1DCRenderTarget*

傳回 ID2D1DCRenderTarget 介面

```
operator ID2D1DCRenderTarget*();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化,則指向 ID2D1DCRenderTarget 介面或 NULL 的指標。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)

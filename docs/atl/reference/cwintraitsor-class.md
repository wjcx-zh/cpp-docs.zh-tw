---
title: CWinTraitsOR 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CWinTraitsOR
- ATLWIN/ATL::CWinTraitsOR
- ATLWIN/ATL::CWinTraitsOR::GetWndExStyle
- ATLWIN/ATL::CWinTraitsOR::GetWndStyle
dev_langs:
- C++
helpviewer_keywords:
- CWinTraitsOR class
- window styles, default values for ATL
ms.assetid: 1eb7b1e8-a9bd-411b-a30a-35a8a10af989
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3883065d9d7222d5e9d98806f0baadf0bc209213
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50072300"
---
# <a name="cwintraitsor-class"></a>CWinTraitsOR 類別

這個類別提供的方法標準化建立視窗物件時所使用的樣式。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
template <DWORD t_dwStyle = 0,
          DWORD t_dwExStyle = 0,
          class TWinTraits = CControlWinTraits>
class CWinTraitsOR
```

#### <a name="parameters"></a>參數

*t_dwStyle*<br/>
預設的視窗樣式。

*t_dwExStyle*<br/>
預設延伸的視窗樣式。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CWinTraitsOR::GetWndExStyle](#getwndexstyle)|擷取的擴充的樣式`CWinTraitsOR`物件。|
|[CWinTraitsOR::GetWndStyle](#getwndstyle)|擷取標準樣式`CWinTraitsOR`物件。|

## <a name="remarks"></a>備註

這[視窗特性](../../atl/understanding-window-traits.md)類別提供簡單的方法標準化用於建立 ATL 視窗物件的樣式。 使用此類別的特製化，做為範本參數[CWindowImpl](../../atl/reference/cwindowimpl-class.md)或 ATL 的視窗類別，來指定要用於標準與擴充樣式的最小集合的另一個該視窗類別的執行個體。

如果您想要確定特定樣式設定視窗類別的所有執行個體同時允許其他樣式設定的呼叫中以個別執行個體為基礎，請使用此樣板的特製化[CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create)。

如果您想要提供預設會在呼叫中不指定任何其他樣式時使用的視窗樣式`CWindowImpl::Create`，使用[CWinTraits](../../atl/reference/cwintraits-class.md)改。

## <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="getwndstyle"></a>  CWinTraitsOR::GetWndStyle

呼叫此函式可擷取 （使用邏輯 OR 運算子） 的標準樣式的組合`CWinTraits`物件和所指定的預設樣式*t_dwStyle*。

```
static DWORD GetWndStyle(DWORD dwStyle);
```

### <a name="parameters"></a>參數

*cheaderctrl:: Create*<br/>
用於建立視窗的樣式。

### <a name="return-value"></a>傳回值

傳入的樣式的組合*cheaderctrl:: Create* ，預設值是由`t_dwStyle`，使用邏輯 OR 運算子。

##  <a name="getwndexstyle"></a>  CWinTraitsOR::GetWndExStyle

呼叫此函式可擷取 （使用邏輯 OR 運算子） 的延伸樣式的組合`CWinTraits`物件和所指定的預設樣式`t_dwStyle`。

```
static DWORD GetWndExStyle(DWORD dwExStyle);
```

### <a name="parameters"></a>參數

*dwExStyle*<br/>
用來建立視窗的延伸的樣式。

### <a name="return-value"></a>傳回值

傳入的延伸樣式的組合*dwExStyle*所指定的預設和`t_dwExStyle`，使用邏輯 OR 運算子

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)<br/>
[了解視窗特性](../../atl/understanding-window-traits.md)


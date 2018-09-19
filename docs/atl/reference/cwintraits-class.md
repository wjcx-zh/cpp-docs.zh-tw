---
title: CWinTraits 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CWinTraits
- ATLWIN/ATL::CWinTraits
- ATLWIN/ATL::CWinTraits::GetWndExStyle
- ATLWIN/ATL::CWinTraits::GetWndStyle
dev_langs:
- C++
helpviewer_keywords:
- CMDIChildWinTraits class
- window styles, default values for ATL
- CWinTraits class
- CFrameWinTraits class
- CControlWinTraits class
ms.assetid: f78f486e-6d9c-42c6-8e86-371e05aa7e59
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fb6ee8cd591c4a5b5a4a3701c6974849f9e3238f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46069388"
---
# <a name="cwintraits-class"></a>CWinTraits 類別

這個類別提供的方法標準化建立視窗物件時所使用的樣式。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
template <DWORD t_dwStyle = 0, DWORD t_dwExStyle = 0>  class CWinTraits
```

#### <a name="parameters"></a>參數

*t_dwStyle*<br/>
預設的標準的視窗樣式。

*t_dwExStyle*<br/>
預設延伸的視窗樣式。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CWinTraits::GetWndExStyle](#getwndexstyle)|（靜態）擷取的擴充的樣式`CWinTraits`物件。|
|[CWinTraits::GetWndStyle](#getwndstyle)|（靜態）擷取標準樣式`CWinTraits`物件。|

## <a name="remarks"></a>備註

這[視窗特性](../../atl/understanding-window-traits.md)類別提供簡單的方法標準化用於建立 ATL 視窗物件的樣式。 使用此類別的特製化，做為範本參數[CWindowImpl](../../atl/reference/cwindowimpl-class.md)或另一個 ATL 的視窗類別，來指定所使用的預設標準與擴充樣式的視窗類別的執行個體。

使用此範本，當您想要提供預設會在呼叫中不指定任何其他樣式時使用的視窗樣式[CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create)。

ATL 提供三個預先定義的樣板的特製化此常用的視窗樣式的組合：

- `CControlWinTraits`  

   專為標準控制項的視窗。 使用下列標準樣式： WS_CHILD、 WS_VISIBLE、 WS_CLIPCHILDREN 和 WS_CLIPSIBLINGS。 沒有延伸的樣式。

- `CFrameWinTraits`  

   專為標準的框架視窗。 包含所使用的標準樣式： WS_OVERLAPPEDWINDOW、 WS_CLIPCHILDREN 和 WS_CLIPSIBLINGS。 包含用於延伸的樣式： WS_EX_APPWINDOW 和 WS_EX_WINDOWEDGE。

- `CMDIChildWinTraits`  

   專為標準的 MDI 子視窗。 包含所使用的標準樣式： WS_OVERLAPPEDWINDOW、 WS_CHILD、 WS_VISIBLE、 WS_CLIPCHILDREN 和 WS_CLIPSIBLINGS。 包含用於延伸的樣式： WS_EX_MDICHILD。

如果您想要確保特定樣式所設定的所有執行個體同時允許要在每個執行個體為基礎，設定其他樣式的視窗類別使用[CWinTraitsOR](../../atl/reference/cwintraitsor-class.md)改。

## <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="getwndstyle"></a>  CWinTraits::GetWndStyle

呼叫此函式可擷取的標準樣式`CWinTraits`物件。

```
static DWORD GetWndStyle(DWORD dwStyle);
```

### <a name="parameters"></a>參數

*cheaderctrl:: Create*<br/>
用來建立視窗的標準的樣式。 如果*cheaderctrl:: Create*為 0，範本的樣式值 (`t_dwStyle`) 會傳回。 如果*cheaderctrl:: Create*為非零值， *cheaderctrl:: Create*會傳回。

### <a name="return-value"></a>傳回值

物件的標準的視窗樣式。

##  <a name="getwndexstyle"></a>  CWinTraits::GetWndExStyle

呼叫此函式可擷取的擴充的樣式`CWinTraits`物件。

```
static DWORD GetWndExStyle(DWORD dwExStyle);
```

### <a name="parameters"></a>參數

*dwExStyle*<br/>
用來建立視窗的延伸的樣式。 如果*dwExStyle*為 0，範本的樣式值 (`t_dwExStyle`) 會傳回。 如果*dwExStyle*為非零值， *dwExStyle*會傳回。

### <a name="return-value"></a>傳回值

物件的延伸的視窗樣式。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)<br/>
[了解視窗特性](../../atl/understanding-window-traits.md)

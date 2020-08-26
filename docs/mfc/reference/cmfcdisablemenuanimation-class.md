---
title: CMFCDisableMenuAnimation 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCDisableMenuAnimation
- AFXPOPUPMENU/CMFCDisableMenuAnimation
- AFXPOPUPMENU/CMFCDisableMenuAnimation::Restore
helpviewer_keywords:
- CMFCDisableMenuAnimation [MFC], Restore
ms.assetid: c6eb07da-c382-43d6-8028-007f2320e50e
ms.openlocfilehash: 97a93e000b3e12d8ec4824100059581216b1b8d9
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840761"
---
# <a name="cmfcdisablemenuanimation-class"></a>CMFCDisableMenuAnimation 類別

停用快顯功能表動畫。

## <a name="syntax"></a>語法

```
class CMFCDisableMenuAnimation
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|-|-|
|`CMFCDisableMenuAnimation::CMFCDisableMenuAnimation`|建構 `CMFCDisableMenuAnimation` 物件。|
|`CMFCDisableMenuAnimation::~CMFCDisableMenuAnimation`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|-|-|
|[CMFCDisableMenuAnimation：： Restore](#restore)|還原 framework 用來顯示快顯功能表的先前動畫。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|-|-|
|`CMFCDisableMenuAnimation::m_animType`|儲存先前的快顯功能表動畫類型。|

### <a name="remarks"></a>備註

您可以使用此協助程式類別來暫時停用快顯功能表動畫 (例如，當您處理滑鼠或鍵盤命令時) 。

`CMFCDisableMenuAnimation`物件會在其存留期內停用快顯功能表動畫。 此函式會將目前的快顯功能表動畫類型儲存在 `m_animType` 欄位中，並將目前的動畫類型設定為 `CMFCPopupMenu::NO_ANIMATION` 。 此函式會還原先前的動畫類型。

您可以 `CMFCDisableMenuAnimation` 在堆疊上建立物件，以在整個單一函式中停用快顯功能表動畫。 如果您想要停用函式之間的快顯功能表動畫，請 `CMFCDisableMenuAnimation` 在堆積上建立物件，然後在您想要還原快顯功能表動畫時刪除它。

## <a name="example"></a>範例

下列範例顯示如何使用堆疊來暫時停用功能表動畫。

[!code-cpp[NVC_MFC_Misc#1](../../mfc/reference/codesnippet/cpp/cmfcdisablemenuanimation-class_1.h)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CMFCDisableMenuAnimation](../../mfc/reference/cmfcdisablemenuanimation-class.md)

## <a name="requirements"></a>規格需求

**標頭：** afxpopupmenu。h

## <a name="cmfcdisablemenuanimationrestore"></a><a name="restore"></a> CMFCDisableMenuAnimation：： Restore

還原 framework 用來顯示快顯功能表的先前動畫。

```cpp
void Restore ();
```

### <a name="remarks"></a>備註

此函式會呼叫這個方法， `CMFCDisableMenuAnimation` 以還原 framework 用來顯示快顯功能表的先前動畫。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPopupMenu 類別](../../mfc/reference/cmfcpopupmenu-class.md)

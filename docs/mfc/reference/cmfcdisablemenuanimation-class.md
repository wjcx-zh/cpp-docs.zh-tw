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
ms.openlocfilehash: bf8c598e9e105569e0a5676267e205b3d3939712
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62345600"
---
# <a name="cmfcdisablemenuanimation-class"></a>CMFCDisableMenuAnimation 類別

停用快顯功能表的動畫。

## <a name="syntax"></a>語法

```
class CMFCDisableMenuAnimation
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|||
|-|-|
|名稱|描述|
|`CMFCDisableMenuAnimation::CMFCDisableMenuAnimation`|建構 `CMFCDisableMenuAnimation` 物件。|
|`CMFCDisableMenuAnimation::~CMFCDisableMenuAnimation`|解構函式。|

### <a name="public-methods"></a>公用方法

|||
|-|-|
|名稱|描述|
|[CMFCDisableMenuAnimation::Restore](#restore)|還原前一個動畫架構用來顯示快顯功能表。|

### <a name="data-members"></a>資料成員

|||
|-|-|
|名稱|描述|
|`CMFCDisableMenuAnimation::m_animType`|會儲存先前的快顯功能表動畫類型。|

### <a name="remarks"></a>備註

您可以使用這個 helper 類別，暫時停用快顯功能表動畫，（例如，當您處理滑鼠或鍵盤命令）。

A`CMFCDisableMenuAnimation`物件停用快顯功能表動畫在其存留期間。 建構函式會儲存在目前的快顯功能表動畫類型`m_animType`欄位和目前的動畫類型的集合`CMFCPopupMenu::NO_ANIMATION`。 解構函式會還原先前的動畫類型。

您可以建立`CMFCDisableMenuAnimation`停用快顯功能表動畫，單一函式在堆疊上的物件。 如果您想要停用快顯功能表動畫，函式之間，建立`CMFCDisableMenuAnimation`物件在堆積上，然後再將之刪除當您想要還原的快顯功能表的動畫。

## <a name="example"></a>範例

下列範例示範如何使用堆疊暫時停用功能表動畫。

[!code-cpp[NVC_MFC_Misc#1](../../mfc/reference/codesnippet/cpp/cmfcdisablemenuanimation-class_1.h)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CMFCDisableMenuAnimation](../../mfc/reference/cmfcdisablemenuanimation-class.md)

## <a name="requirements"></a>需求

**標頭：** afxpopupmenu.h

##  <a name="restore"></a>  CMFCDisableMenuAnimation::Restore

還原前一個動畫架構用來顯示快顯功能表。

```
void Restore ();
```

### <a name="remarks"></a>備註

這個方法會呼叫`CMFCDisableMenuAnimation`還原架構用來顯示快顯功能表的上一個動畫的解構函式。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPopupMenu 類別](../../mfc/reference/cmfcpopupmenu-class.md)

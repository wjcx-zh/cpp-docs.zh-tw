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
ms.openlocfilehash: 990f41d2dfa6491d246797322ee275c9648d52a9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367575"
---
# <a name="cmfcdisablemenuanimation-class"></a>CMFCDisableMenuAnimation 類別

禁用彈出式功能表動畫。

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
|[CMFC禁用功能表動畫::恢復](#restore)|還原框架用於顯示彈出式功能表的上一個動畫。|

### <a name="data-members"></a>資料成員

|||
|-|-|
|名稱|描述|
|`CMFCDisableMenuAnimation::m_animType`|存儲以前的彈出式功能表動畫類型。|

### <a name="remarks"></a>備註

使用此幫助器類可暫時禁用彈出式功能表動畫(例如,處理滑鼠或鍵盤命令時)。

對`CMFCDisableMenuAnimation`象 在其生存期內禁用彈出式功能表動畫。 建構函數將目前彈出式選單動畫型態儲存在欄位中`m_animType`, 並將目前的動畫類型`CMFCPopupMenu::NO_ANIMATION`設定為 。 析構函數還原以前的動畫類型。

您可以在堆疊上`CMFCDisableMenuAnimation`創建物件,以在整個單個函數中禁用彈出功能表動畫。 如果要在函數之間禁用彈出功能表動畫,請在堆上創建`CMFCDisableMenuAnimation`一個物件,然後在要還原彈出菜單動畫時將其刪除。

## <a name="example"></a>範例

下面的示例演示如何使用堆疊臨時禁用功能表動畫。

[!code-cpp[NVC_MFC_Misc#1](../../mfc/reference/codesnippet/cpp/cmfcdisablemenuanimation-class_1.h)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CMFC禁用選單動畫](../../mfc/reference/cmfcdisablemenuanimation-class.md)

## <a name="requirements"></a>需求

**標題:** afxpopupmenu.h

## <a name="cmfcdisablemenuanimationrestore"></a><a name="restore"></a>CMFC禁用功能表動畫::恢復

還原框架用於顯示彈出式功能表的上一個動畫。

```
void Restore ();
```

### <a name="remarks"></a>備註

`CMFCDisableMenuAnimation`析構函數調用此方法以還原框架用於顯示彈出式功能表的上一個動畫。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPopupMenu 類別](../../mfc/reference/cmfcpopupmenu-class.md)

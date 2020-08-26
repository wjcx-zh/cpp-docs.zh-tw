---
title: CMDITabInfo 類別
ms.date: 11/04/2016
f1_keywords:
- CMDITabInfo
- AFXMDICLIENTAREAWND/CMDITabInfo
- AFXMDICLIENTAREAWND/CMDITabInfo::Serialize
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bAutoColor
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bDocumentMenu
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bEnableTabSwap
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bFlatFrame
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabCloseButton
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabCustomTooltips
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabIcons
- AFXMDICLIENTAREAWND/CMDITabInfo::m_nTabBorderSize
- AFXMDICLIENTAREAWND/CMDITabInfo::m_style
- AFXMDICLIENTAREAWND/CMDITabInfo::m_tabLocation
helpviewer_keywords:
- CMDITabInfo [MFC], Serialize
- CMDITabInfo [MFC], m_bAutoColor
- CMDITabInfo [MFC], m_bDocumentMenu
- CMDITabInfo [MFC], m_bEnableTabSwap
- CMDITabInfo [MFC], m_bFlatFrame
- CMDITabInfo [MFC], m_bTabCloseButton
- CMDITabInfo [MFC], m_bTabCustomTooltips
- CMDITabInfo [MFC], m_bTabIcons
- CMDITabInfo [MFC], m_nTabBorderSize
- CMDITabInfo [MFC], m_style
- CMDITabInfo [MFC], m_tabLocation
ms.assetid: 988ae1b7-4f7f-4239-b88f-7e28b3291c5e
ms.openlocfilehash: 8e4053bf16672d693adc104c9e88bb46a67ba7dd
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845909"
---
# <a name="cmditabinfo-class"></a>CMDITabInfo 類別

`CMDITabInfo`類別是用來將參數傳遞至[CMDIFrameWndEx：： EnableMDITabbedGroups](../../mfc/reference/cmdiframewndex-class.md#enablemditabbedgroups)方法。 設定這個類別的成員以控制 MDI 索引標籤式群組的行為。

## <a name="syntax"></a>語法

```
class CMDITabInfo
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|`CMDITabInfo::CMDITabInfo`|預設建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMDITabInfo：：序列化](#serialize)|從封存中讀取或寫入此物件。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[CMDITabInfo：： m_bActiveTabCloseButton;](#m_bactivetabclosebutton_)|指定 [使用中] 索引標籤的標籤上是否顯示 [ **關閉** ] 按鈕。|
|[CMDITabInfo：： m_bAutoColor](#m_bautocolor)|指定是否要為 MDI 索引標籤上色。|
|[CMDITabInfo：： m_bDocumentMenu](#m_bdocumentmenu)|指定索引標籤群組是否顯示顯示已開啟檔案清單或顯示捲軸按鈕的快顯功能表。|
|[CMDITabInfo：： m_bEnableTabSwap](#m_benabletabswap)|指定使用者是否可以藉由拖曳來交換索引標籤的位置。|
|[CMDITabInfo：： m_bFlatFrame](#m_bflatframe)|指定索引標籤是否有平面框架。|
|[CMDITabInfo：： m_bTabCloseButton](#m_btabclosebutton)|指定每個索引標籤標籤是否顯示 [ **關閉** ] 按鈕。|
|[CMDITabInfo：： m_bTabCustomTooltips](#m_btabcustomtooltips)|指定是否啟用自訂工具提示。|
|[CMDITabInfo：： m_bTabIcons](#m_btabicons)|指定是否要在 MDI 索引標籤上顯示圖示。|
|[CMDITabInfo：： m_nTabBorderSize](#m_ntabbordersize)|指定每個索引標籤視窗的框線大小。|
|[CMDITabInfo：： m_style](#m_style)|指定索引標籤標籤的樣式。|
|[CMDITabInfo：： m_tabLocation](#m_tablocation)|指定索引標籤標籤是否位於頁面的頂端或底部。|

## <a name="remarks"></a>備註

這個類別會指定架構所建立的 MDI 索引標籤群組參數。

## <a name="example"></a>範例

下列範例示範如何在類別中設定各種成員變數的值 `CMDITabInfo` 。

[!code-cpp[NVC_MFC_MDITab#1](../../mfc/reference/codesnippet/cpp/cmditabinfo-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CMDITabInfo](../../mfc/reference/cmditabinfo-class.md)

## <a name="requirements"></a>規格需求

**標頭：** afxmdiclientareawnd。h

## <a name="cmditabinfom_bactivetabclosebutton"></a><a name="m_bactivetabclosebutton_"></a> CMDITabInfo：： m_bActiveTabCloseButton;

指定 [使用中] 索引標籤的標籤上是否顯示 [ **關閉** ] 按鈕。

```
BOOL m_bActiveTabCloseButton;
```

### <a name="remarks"></a>備註

若為 TRUE，使用中索引標籤的標籤將會顯示 [ **關閉** ] 按鈕。 [ **關閉** ] 按鈕將會從索引標籤區域的右上角移除。 否則，[使用中] 索引標籤的標籤不會顯示 [ **關閉** ] 按鈕。 [ **關閉** ] 按鈕會出現在索引標籤區域的右上角。

## <a name="cmditabinfom_bautocolor"></a><a name="m_bautocolor"></a> CMDITabInfo：： m_bAutoColor

指定每個 MDI 索引標籤是否有自己的色彩。

```
BOOL m_bAutoColor;
```

### <a name="remarks"></a>備註

若為 TRUE，則每個索引標籤會有自己的色彩。 這組色彩是由 MFC 程式庫所管理。 否則，索引標籤會以白色顯示。 預設值為 FALSE。

## <a name="cmditabinfom_bdocumentmenu"></a><a name="m_bdocumentmenu"></a> CMDITabInfo：： m_bDocumentMenu

指定每個索引標籤是否會顯示快顯功能表，其中會顯示位於索引標籤區域右側的已開啟檔案清單。

```
BOOL m_bDocumentMenu;
```

### <a name="remarks"></a>備註

若為 TRUE，則每個索引標籤視窗會顯示快顯功能表，其中會顯示位於索引標籤區域右邊緣的已開啟檔案清單;否則，索引標籤視窗會在索引標籤區域的右邊緣顯示滾動按鈕。 預設值為 FALSE。

## <a name="cmditabinfom_benabletabswap"></a><a name="m_benabletabswap"></a> CMDITabInfo：： m_bEnableTabSwap

指定使用者是否可以藉由拖曳來交換索引標籤的位置。

```
BOOL m_bEnableTabSwap;
```

### <a name="remarks"></a>備註

若為 TRUE，使用者可以拖曳索引標籤來變更索引標籤位置。 否則，使用者將無法變更索引標籤位置。 預設值為 TRUE。

## <a name="cmditabinfom_bflatframe"></a><a name="m_bflatframe"></a> CMDITabInfo：： m_bFlatFrame

指定每個索引標籤視窗是否都有平面框架。

```
BOOL m_bFlatFrame;
```

## <a name="cmditabinfom_btabclosebutton"></a><a name="m_btabclosebutton"></a> CMDITabInfo：： m_bTabCloseButton

指定每個索引標籤視窗是否顯示 [ **關閉** ] 按鈕。

```
BOOL m_bTabCloseButton;
```

### <a name="remarks"></a>備註

若為 TRUE，則每個索引標籤視窗會在索引標籤的右邊緣顯示 [ **關閉** ] 按鈕。否則，就不會顯示 [ **關閉** ] 按鈕。 預設值為 TRUE。

## <a name="cmditabinfom_btabcustomtooltips"></a><a name="m_btabcustomtooltips"></a> CMDITabInfo：： m_bTabCustomTooltips

指定索引標籤是否顯示工具提示。

```
BOOL m_bTabCustomTooltips;
```

### <a name="remarks"></a>備註

若為 TRUE，則應用程式會將 AFX_WM_ON_GET_TAB_TOOLTIP 訊息傳送至主框架。 您可以使用 ON_REGISTERED_MESSAGE 宏來處理此訊息。

## <a name="cmditabinfom_btabicons"></a><a name="m_btabicons"></a> CMDITabInfo：： m_bTabIcons

指定是否要在 MDI 索引標籤上顯示圖示。

```
BOOL m_bTabIcons;
```

### <a name="remarks"></a>備註

若為 TRUE，則會在每個 MDI 索引標籤上顯示圖示，否則圖示不會顯示在索引標籤上。 預設值為 FALSE。

## <a name="cmditabinfom_ntabbordersize"></a><a name="m_ntabbordersize"></a> CMDITabInfo：： m_nTabBorderSize

指定每個索引標籤視窗的框線大小（以圖元為單位）。

```
int m_nTabBorderSize;
```

### <a name="remarks"></a>備註

[CMFCVisualManager：： GetMDITabsBordersSize](../../mfc/reference/cmfcvisualmanager-class.md#getmditabsborderssize) 會傳回預設值。

## <a name="cmditabinfom_style"></a><a name="m_style"></a> CMDITabInfo：： m_style

指定索引標籤標籤的樣式。

```
CMFCTabCtrl::Style m_style
```

### <a name="remarks"></a>備註

針對索引標籤標籤指定下列其中一種樣式：

|巨集|描述|
|-|-|
|STYLE_3D|3D 樣式。  |
|STYLE_3D_ONENOTE|Microsoft OneNote 樣式。  |
|STYLE_3D_VS2005|Microsoft Visual Studio 2005 樣式。  |
|STYLE_3D_SCROLLED|具有矩形制表符標籤的3D 樣式。  |
|STYLE_FLAT_SHARED_HORZ_SCROLL|具有共用水準捲軸的平面樣式。  |
|STYLE_3D_ROUNDED_SCROLL|具有圓形制表符標籤的3D 樣式。  |

## <a name="cmditabinfom_tablocation"></a><a name="m_tablocation"></a> CMDITabInfo：： m_tabLocation

指定索引標籤標籤是否位於頁面的頂端或底部。

```
CMFCTabCtrl::Location m_tabLocation;
```

### <a name="remarks"></a>備註

將下列其中一個位置旗標套用至索引標籤：

- LOCATION_BOTTOM：索引標籤標籤位於頁面底部。

- LOCATION_TOP：標籤標籤位於頁面頂端

## <a name="cmditabinfoserialize"></a><a name="serialize"></a> CMDITabInfo：：序列化

從封存或封存讀取或寫入此物件。

```cpp
void Serialize(CArchive& ar);
```

### <a name="parameters"></a>參數

*Ar*<br/>
在要序列化的 [CArchive 類別](../../mfc/reference/carchive-class.md) 物件。

## <a name="see-also"></a>另請參閱

[CMDIFrameWndEx 類別](../../mfc/reference/cmdiframewndex-class.md)<br/>
[MDI 索引標籤式群組](../../mfc/mdi-tabbed-groups.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)

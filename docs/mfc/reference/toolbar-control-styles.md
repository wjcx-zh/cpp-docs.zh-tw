---
title: ToolBar 控制項樣式
ms.date: 11/04/2016
helpviewer_keywords:
- ToolBar control styles [MFC]
ms.assetid: 0f717eb9-fa32-4263-b852-809238863feb
ms.openlocfilehash: f26edc6c0ce4a19528a9a8754428411318e9b9d2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648990"
---
# <a name="toolbar-control-styles"></a>ToolBar 控制項樣式

[CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)具有一組決定外觀的樣式旗標和按鈕的行為。 您可以藉由呼叫設定這些旗標的組合[CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle)。 本主題列出樣式旗標值及其意義。

## <a name="property-values"></a>屬性值

下列值可決定控制項所代表按鈕的類型：

|||
|-|-|
|TBBS_BUTTON|標準按鈕 (預設值)。  |
|TBBS_CHECKBOX|核取方塊。  |
|TBBS_CHECKGROUP|核取方塊群組的開頭。  |
|TBBS_GROUP|按鈕群組的開頭。  |
|TBBS_SEPARATOR|分隔符號。  |

下列值表示控制項的目前狀態：

|||
|-|-|
|TBBS_CHECKED|核取方塊已核取。  |
|TBBS_DISABLED|控制項已停用。  |
|TBBS_INDETERMINATE|核取方塊處於不定狀態。  |
|TBBS_PRESSED|按鈕已按下。  |

下列值可變更工具列中按鈕的配置：

|||
|-|-|
|TBBS_BREAK|將項目放置在新的一行或一欄中，而不分隔資料行。  |

## <a name="remarks"></a>備註

目前的樣式會儲存在[CMFCToolBarButton::m_nStyle](../../mfc/reference/cmfctoolbarbutton-class.md#m_nstyle)。 中未設定為新的值`m_nStyle`直接管理，因為某些衍生的類別可讓您執行其他處理，當您呼叫`SetStyles`。

視覺管理員會決定每個狀態下的按鈕外觀。 請參閱[視覺化管理員](../../mfc/visualization-manager.md)如需詳細資訊。

## <a name="requirements"></a>需求

**標頭：** afxtoolbarbutton.h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[視覺化管理員](../../mfc/visualization-manager.md)


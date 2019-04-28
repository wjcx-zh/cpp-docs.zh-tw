---
title: COleControlModule 類別
ms.date: 11/04/2016
f1_keywords:
- OleControlModule
helpviewer_keywords:
- OLE control modules [MFC]
- MFC ActiveX controls [MFC], OLE control modules
- COleControlModule class [MFC]
- control modules [MFC]
ms.assetid: 0721724d-d4af-4eda-ad34-5a2b27810dd4
ms.openlocfilehash: f6d486c7bacb897d70d85414ac3d0bd0d13e447b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62310392"
---
# <a name="colecontrolmodule-class"></a>COleControlModule 類別

OLE 控制項模組物件所衍生自的基底類別。

## <a name="syntax"></a>語法

```
class COleControlModule : public CWinApp
```

## <a name="remarks"></a>備註

這個類別提供成員函式初始化控制項模組。 使用 Microsoft Foundation classes 的每個 OLE 控制項模組只能包含一個物件衍生自`COleControlModule`。 此物件建構時其他C++建構全域物件。 宣告您的衍生`COleControlModule`全域層級的物件。

如需有關使用`COleControlModule`類別，請參閱[CWinApp](../../mfc/reference/cwinapp-class.md)類別與發行項[ActiveX 控制項](../../mfc/mfc-activex-controls.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWinThread](../../mfc/reference/cwinthread-class.md)

[CWinApp](../../mfc/reference/cwinapp-class.md)

`COleControlModule`

## <a name="requirements"></a>需求

**標頭：** afxctl.h

## <a name="see-also"></a>另請參閱

[MFC 範例 TESTHELP](../../overview/visual-cpp-samples.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)

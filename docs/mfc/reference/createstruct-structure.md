---
title: CREATESTRUCT 結構
ms.date: 11/04/2016
f1_keywords:
- CREATESTRUCT
helpviewer_keywords:
- CREATESTRUCT structure [MFC]
ms.assetid: 028c7b5e-4fdc-48da-a550-d3e4f9e6cc85
ms.openlocfilehash: 1de42ba3e26f7a06918a69358083e68f142836cc
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694695"
---
# <a name="createstruct-structure"></a>CREATESTRUCT 結構

`CREATESTRUCT`結構會定義初始化參數傳遞至應用程式的視窗程序。

## <a name="syntax"></a>語法

```
typedef struct tagCREATESTRUCT {
    LPVOID lpCreateParams;
    HANDLE hInstance;
    HMENU hMenu;
    HWND hwndParent;
    int cy;
    int cx;
    int y;
    int x;
    LONG style;
    LPCSTR lpszName;
    LPCSTR lpszClass;
    DWORD dwExStyle;
} CREATESTRUCT;
```

#### <a name="parameters"></a>參數

*lpCreateParams*<br/>
要用來建立視窗的資料點。

*hInstance*<br/>
識別擁有新的視窗之模組的模組執行個體控制代碼。

*hMenu*<br/>
識別可供新的視窗功能表。 如果子視窗，包含整數識別碼。

*hwndParent*<br/>
識別擁有新的視窗的視窗。 如果新的視窗是最上層視窗，這個成員會是 NULL。

*cy*<br/>
指定新的視窗的高度。

*cx*<br/>
指定新的視窗的寬度。

*y*<br/>
指定新的視窗左上角的 y 座標。 新的視窗是子視窗; 如果座標是相對於父視窗否則，座標是相對於螢幕的原點。

*x*<br/>
指定新的視窗左上角的 x 座標。 新的視窗是子視窗; 如果座標是相對於父視窗否則，座標是相對於螢幕的原點。

*style*<br/>
指定新的視窗[樣式](../../mfc/reference/styles-used-by-mfc.md)。

*lpszName*<br/>
指向以 null 終止的字串，指定新的視窗名稱。

*lpszClass*<br/>
指向以 null 終止的字串，指定新的視窗 Windows 類別名稱 ( [WNDCLASS](/windows/desktop/api/winuser/ns-winuser-tagwndclassa)結構; 如需詳細資訊，請參閱 Windows SDK)。

*dwExStyle*<br/>
指定[延伸樣式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)新視窗。

## <a name="requirements"></a>需求

**標頭：** winuser.h

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnCreate](../../mfc/reference/cwnd-class.md#oncreate)


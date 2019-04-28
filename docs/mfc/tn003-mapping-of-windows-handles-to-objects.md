---
title: TN003:將 Windows 控制代碼對應到物件
ms.date: 11/04/2016
f1_keywords:
- vc.mapping
helpviewer_keywords:
- TN003
- handle maps
- Windows handles to objects [MFC]
- mappings [MFC], Windows handles to objects
ms.assetid: fbea9f38-992c-4091-8dbc-f29e288617d6
ms.openlocfilehash: e7844398ebaf5a8fdf8c56ab18b33d8c7717d1ad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62306365"
---
# <a name="tn003-mapping-of-windows-handles-to-objects"></a>TN003:將 Windows 控制代碼對應到物件

本提示描述 MFC 常式，它支援對應 Windows 物件控制代碼C++物件。

## <a name="the-problem"></a>問題

Windows 物件都通常由各種[處理](/windows/desktop/WinProg/windows-data-types)物件的 MFC 類別包裝 Windows 物件控制代碼並且C++物件。 包裝函式的 MFC 類別程式庫的控制代碼可讓您找出C++包裝 Windows 物件具有特定的控制代碼的物件。 不過，有時候物件沒有C++包裝函式物件，並在這些時間，系統會建立暫存的物件，以做為C++包裝函式。

Windows 物件的處理常式對應如下所示：

- HWND ([CWnd](../mfc/reference/cwnd-class.md)和`CWnd`-衍生的類別)

- HDC ([CDC](../mfc/reference/cdc-class.md)和`CDC`-衍生的類別)

- HMENU ([CMenu](../mfc/reference/cmenu-class.md))

- HPEN ([CGdiObject](../mfc/reference/cgdiobject-class.md))

- HBRUSH (`CGdiObject`)

- HFONT (`CGdiObject`)

- HBITMAP (`CGdiObject`)

- HPALETTE (`CGdiObject`)

- HRGN (`CGdiObject`)

- HIMAGELIST ([CImageList](../mfc/reference/cimagelist-class.md))

- 通訊端 ([CSocket](../mfc/reference/csocket-class.md))

假設這些物件的任何一個控制代碼，您可以找到 MFC 包裝之物件的控制代碼藉由呼叫靜態方法`FromHandle`。 例如，假設呼叫 HWND *hWnd*下, 面這一行會傳回的指標`CWnd`包裝*hWnd*:

```
CWnd::FromHandle(hWnd)
```

如果*hWnd*沒有特定的包裝函式物件，暫時`CWnd`用來包裝*hWnd*。 這讓您能夠取得有效C++從任何控制代碼的物件。

包裝函式物件之後，您可以從包裝函式類別的公用成員變數來擷取其控制代碼。 若是`CWnd`， *m_hWnd*包含該物件的 HWND。

## <a name="attaching-handles-to-mfc-objects"></a>附加至 MFC 物件的控制代碼

Windows 物件，指定新建立的控制代碼的包裝函式物件和控制代碼，您可以將這兩個藉由呼叫`Attach`函式，如此範例所示：

```
CWnd myWnd;
myWnd.Attach(hWnd);
```

如此一來項目中永久對應建立關聯*myWnd*並*hWnd*。 呼叫`CWnd::FromHandle(hWnd)`現在會傳回的指標*myWnd*。 當*myWnd*已刪除，解構函式會自動終結*hWnd*藉由呼叫 Windows [DestroyWindow](/windows/desktop/api/winuser/nf-winuser-destroywindow)函式。 如果不需要這項目，則*hWnd*必須從中斷連結*myWnd*之前*myWnd*終結 (通常在離開範圍時，才*myWnd*所定義)。 `Detach`方法的做法。

```
myWnd.Detach();
```

## <a name="more-about-temporary-objects"></a>深入了解暫存物件

建立暫存物件的每次`FromHandle`有尚未有包裝函式物件的控制代碼。 從其控制代碼中斷連結並刪除這些暫存物件`DeleteTempMap`函式。 依預設[CWinThread::OnIdle](../mfc/reference/cwinthread-class.md#onidle)會自動呼叫`DeleteTempMap`支援暫存的控制代碼對應每個類別。 這表示您不能假設暫存物件的指標就會是有效遠從函式的結束點已取得指標的位置。

## <a name="wrapper-objects-and-multiple-threads"></a>包裝函式物件和多個執行緒

暫時性和永久性的物件會維護每個執行緒為基礎。 也就是說，一個執行緒無法存取另一個執行緒的C++包裝函式物件，無論是暫時性或永久性。

若要從一個執行緒的這些物件傳遞到另一個中，永遠將它們傳送為其原生`HANDLE`型別。 傳遞C++從一個執行緒的包裝函式物件與另一個通常會導致非預期的結果。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)

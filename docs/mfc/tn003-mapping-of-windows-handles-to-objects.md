---
title: TN003：將 Windows 控制碼對應至物件
ms.date: 11/04/2016
f1_keywords:
- vc.mapping
helpviewer_keywords:
- TN003
- handle maps
- Windows handles to objects [MFC]
- mappings [MFC], Windows handles to objects
ms.assetid: fbea9f38-992c-4091-8dbc-f29e288617d6
ms.openlocfilehash: 45492963e1b686e03eb59c320fdc3d52d1534f7d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513533"
---
# <a name="tn003-mapping-of-windows-handles-to-objects"></a>TN003：將 Windows 控制碼對應至物件

此附注描述支援將 Windows 物件控制碼對應至C++物件的 MFC 常式。

## <a name="the-problem"></a>問題

Windows 物件通常是由不同的[控制碼](/windows/win32/WinProg/windows-data-types)物件表示, MFC 類別會使用C++物件包裝 windows 物件控制碼。 MFC 類別庫的控制碼換行函式可讓您C++尋找包裝有特定控制碼之 Windows 物件的物件。 不過, 有時物件並沒有C++包裝函式物件, 而在這些時候, 系統會建立暫存物件以作為C++包裝函式。

使用控制碼對應的 Windows 物件如下所示:

- HWND ([CWnd](../mfc/reference/cwnd-class.md)和`CWnd`衍生類別)

- HDC ([CDC](../mfc/reference/cdc-class.md)和`CDC`衍生類別)

- HMENU ([CMenu](../mfc/reference/cmenu-class.md))

- HPEN ([CGdiObject](../mfc/reference/cgdiobject-class.md))

- HBRUSH (`CGdiObject`)

- HFONT (`CGdiObject`)

- HBITMAP (`CGdiObject`)

- HPALETTE (`CGdiObject`)

- HRGN (`CGdiObject`)

- HIMAGELIST ([CImageList](../mfc/reference/cimagelist-class.md))

- 通訊端 ([CSocket](../mfc/reference/csocket-class.md))

假設有任何一個物件的控制碼, 您可以藉由呼叫靜態方法`FromHandle`來尋找包裝控制碼的 MFC 物件。 例如, 假設有一個稱為*hwnd*的 hwnd, 下面這一行會傳回包裝*HWND*的`CWnd`的指標:

```
CWnd::FromHandle(hWnd)
```

如果*hwnd*沒有特定的包裝函式物件, 就會`CWnd`建立暫存來包裝*hWnd*。 如此一來, 您就可以從C++任何控制碼取得有效的物件。

有了包裝函式物件之後, 您就可以從包裝函式類別的公用成員變數中取出其控制碼。 在的案例`CWnd`中, *m_hWnd*包含該物件的 hWnd。

## <a name="attaching-handles-to-mfc-objects"></a>將控制碼附加至 MFC 物件

針對新建立的控制碼包裝函式物件和 Windows 物件的控制碼, 您可以呼叫`Attach`函數來建立兩者的關聯, 如下列範例所示:

```
CWnd myWnd;
myWnd.Attach(hWnd);
```

這會讓永久對應中的專案與*myWnd*和*hWnd*產生關聯。 呼叫`CWnd::FromHandle(hWnd)`現在會傳回*myWnd*的指標。 當*myWnd*被刪除時, 此函式會藉由呼叫 Windows [DestroyWindow](/windows/win32/api/winuser/nf-winuser-destroywindow)函數, 自動摧毀*hWnd* 。 如果不想要這樣做, 則必須先從*myWnd*卸離*hWnd* , 才能終結*myWnd* (通常會在離開定義*myWnd*的範圍時)。 方法`Detach`會執行此工作。

```
myWnd.Detach();
```

## <a name="more-about-temporary-objects"></a>深入瞭解暫存物件

每當`FromHandle`提供的控制碼尚未有包裝函式物件時, 就會建立暫存物件。 這些暫存物件會從其控制碼卸離, 並`DeleteTempMap`由函數刪除。 根據預設, [CWinThread:: OnIdle](../mfc/reference/cwinthread-class.md#onidle)會`DeleteTempMap`自動呼叫每個支援暫存控制碼對應的類別。 這表示您不能假設暫存物件的指標會在從取得指標的函式結束點之後生效。

## <a name="wrapper-objects-and-multiple-threads"></a>包裝函式物件和多個執行緒

暫時和永久物件都是以每個執行緒為基礎進行維護。 也就是說, 一個執行緒無法存取另一個執行緒的C++包裝函式物件, 不論它是暫時性的還是永久的。

若要將這些物件從一個執行緒傳遞至另一個執行緒, 請一律`HANDLE`將它們當做其原生類型傳送。 將C++包裝函式物件從一個執行緒傳遞至另一個, 通常會導致非預期的結果。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)

---
title: TN017： 終結視窗物件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.objects
dev_langs:
- C++
helpviewer_keywords:
- destroying windows
- TN017
- PostNcDestroy method [MFC]
ms.assetid: 5bf208a5-5683-439b-92a1-547c5ded26cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8286622ec8e7cb739e55a39ce42ed658395551ba
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46407669"
---
# <a name="tn017-destroying-window-objects"></a>TN017：終結視窗物件

此附註將描述使用[CWnd::PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy)方法。 如果您想要執行的自訂的配置，請使用這個方法`CWnd`-衍生物件。 此提示也會說明為什麼您應該使用[cwnd:: Destroywindow](../mfc/reference/cwnd-class.md#destroywindow)終結的 c + + Windows 物件而非**刪除**運算子。

如果您遵循本主題中的指導方針，您會有較少的清除問題。 這些問題可能是因為問題，例如，忘記刪除/釋出 c + + 的記憶體，忘記釋放系統資源，例如`HWND`s，或釋放的物件太多次。

## <a name="the-problem"></a>問題

Windows 中的每個物件 (類別的物件衍生自`CWnd`) 表示這兩個 c + + 物件和`HWND`。 C + + 物件會在應用程式的堆積中配置和`HWND`的視窗管理員所配置的系統資源。 因為有數種方式可終結視窗物件，所以我們必須提供一組規則，導致系統資源或記憶體流失。 這些規則也必須防止物件和 Windows 控制代碼被終結一次以上。

## <a name="destroying-windows"></a>終結 Windows

要終結 Windows 物件的兩個允許的方式如下：

- 呼叫`CWnd::DestroyWindow`或 Windows API `DestroyWindow`。

- 使用明確刪除**刪除**運算子。

第一個案例是到目前為止最常見的。 此案例適用於，即使您的程式碼不會呼叫`DestroyWindow`直接。 當使用者直接關閉框架視窗時，這個動作會產生 WM_CLOSE 訊息，而此訊息的預設回應就是呼叫`DestroyWindow.`父視窗終結時，會呼叫 Windows`DestroyWindow`其所有子系。

第二個案例中，使用**刪除**運算子，在 Windows 的物件，應該很少見。 下列是一些情況下，使用**刪除**是正確的選擇。

## <a name="auto-cleanup-with-cwndpostncdestroy"></a>使用 CWnd::PostNcDestroy 自動清除

系統會終結 Windows 視窗，傳送至視窗的最後一個 Windows 訊息時，控制。 預設值`CWnd`該訊息的處理常式[cwnd::](../mfc/reference/cwnd-class.md#onncdestroy)。 `OnNcDestroy` 將卸離`HWND`c + + 的物件，並呼叫虛擬函式`PostNcDestroy`。 某些類別會覆寫這個函式來刪除 c + + 物件。

預設實作`CWnd::PostNcDestroy`不執行任何動作，這是適合在堆疊框架上配置或內嵌在其他物件的視窗物件。 這不適用於專為可在不含任何其他物件在堆積上配置的視窗物件。 換句話說，它不適用於不會內嵌在其他 c + + 物件的視窗物件。

這些專為單獨在堆積上配置的類別覆寫`PostNcDestroy`方法，以執行**刪除此**。 此陳述式會釋放任何與 c + + 物件相關聯的記憶體。 即使預設`CWnd`解構函式呼叫`DestroyWindow`如果*m_hWnd*是不是 NULL，這不會導致無限遞迴因為控制代碼將清除階段期間會卸離和 NULL。

> [!NOTE]
>  系統通常會呼叫`CWnd::PostNcDestroy`它會處理 Windows 控制訊息之後，`HWND`和 c + + 視窗物件已不再連線。 系統也會呼叫`CWnd::PostNcDestroy`中的大部分實作[cwnd:: Create](../mfc/reference/cwnd-class.md#create)呼叫發生錯誤。 自動清除規則會在本主題稍後所述。

## <a name="auto-cleanup-classes"></a>自動清除類別

下列類別並未設計成自動清除。 它們通常被內嵌在其他 c + + 物件，或在堆疊上：

- 所有標準 Windows 控制項 (`CStatic`， `CEdit`，`CListBox`等等)。

- 任何子視窗直接衍生自`CWnd`（比方說，自訂控制項）。

- 分隔視窗 (`CSplitterWnd`)。

- 預設的控制列 (衍生自`CControlBar`，請參閱 <<c2> [ 技術提示 31](../mfc/tn031-control-bars.md)啟用自動刪除控制列物件)。

- 對話方塊 (`CDialog`) 堆疊框架上的強制回應對話方塊的設計。

- 所有標準都對話方塊除了`CFindReplaceDialog`。

- 類別精靈所建立的預設對話方塊。

下列類別專為自動清除。 它們通常會在堆積上配置本身：

- 主框架視窗 (直接或間接衍生自`CFrameWnd`)。

- 檢視 windows (直接或間接衍生自`CView`)。

如果您想要中斷這些規則，您必須覆寫`PostNcDestroy`衍生類別中的方法。 若要加入您的類別中的自動清除，請呼叫基底類別，然後執行**刪除此**。 若要移除您的類別中的自動清除，請呼叫`CWnd::PostNcDestroy`直接而不是`PostNcDestroy`直接基底類別方法。

變更自動清除行為的常見用法是在堆積上建立非強制回應對話方塊，可配置。

## <a name="when-to-call-delete"></a>要呼叫刪除時

我們建議您呼叫`DestroyWindow`終結 Windows 物件，在 c + + 方法或全域`DestroyWindow`API。

不會呼叫全域`DestroyWindow`終結的 MDI 子視窗的 API。 您應該使用虛擬方法`CWnd::DestroyWindow`改。

C + + 視窗物件，不會執行自動清除，使用**刪除**運算子可能會造成記憶體流失，當您嘗試呼叫`DestroyWindow`在`CWnd::~CWnd`如果 VTBL 不是指向正確的衍生類別的解構函式。 這是因為系統找不到適當的損毀時要呼叫方法。 使用`DestroyWindow`而非**刪除**可避免這些問題。 因為這可能是難以察覺的錯誤，在偵錯模式中編譯會產生下列警告您是否有風險。

```
Warning: calling DestroyWindow in CWnd::~CWnd
    OnDestroy or PostNcDestroy in derived class will not be called
```

在 c + + Windows 執行自動清除的物件，您必須呼叫`DestroyWindow`。 如果您使用**刪除**運算子直接，MFC 診斷記憶體配置器會通知您，您會釋放記憶體兩倍。 兩個項目是您第一次的明確呼叫，並間接呼叫來**刪除此**中的自動清除實作`PostNcDestroy`。

之後呼叫`DestroyWindow`非自動清除物件上的 c + + 物件仍然會但*m_hWnd*會是 NULL。 之後呼叫`DestroyWindow`自動清除物件上的 c + + 物件就會消失，由 c + + delete 運算子，自動清除實作中釋放`PostNcDestroy`。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)


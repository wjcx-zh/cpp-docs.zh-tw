---
title: TN017：終結視窗物件
ms.date: 11/04/2016
f1_keywords:
- vc.objects
helpviewer_keywords:
- destroying windows
- TN017
- PostNcDestroy method [MFC]
ms.assetid: 5bf208a5-5683-439b-92a1-547c5ded26cd
ms.openlocfilehash: 2448a2661851f14fc6fe8747ca19495925442436
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226811"
---
# <a name="tn017-destroying-window-objects"></a>TN017：終結視窗物件

此附注描述[CWnd：:P ostncdestroy](../mfc/reference/cwnd-class.md#postncdestroy)方法的用法。 如果您想要執行自訂的衍生物件配置，請使用這個方法 `CWnd` 。 此附注也會說明為什麼您應該使用[CWnd：:D estroywindow](../mfc/reference/cwnd-class.md#destroywindow)來摧毀 c + + Windows 物件，而不是 **`delete`** 運算子。

如果您遵循本主題中的指導方針，將會有一些清除問題。 這些問題可能是因為忘記刪除/釋放 c + + 記憶體、忘記釋放系統資源（例如 `HWND` ），或釋放物件太多次所造成。

## <a name="the-problem"></a>問題

每個 windows 物件（衍生自之類別的物件 `CWnd` ）都代表 c + + 物件和 `HWND` 。 C + + 物件是在應用程式的堆積中配置，並 `HWND` 由視窗管理員在系統資源中配置。 因為有數種方式可以終結視窗物件，所以我們必須提供一組規則來防止系統資源或記憶體流失。 這些規則也必須防止物件和 Windows 控制碼被終結超過一次。

## <a name="destroying-windows"></a>終結視窗

以下是摧毀 Windows 物件的兩個允許方法：

- 呼叫 `CWnd::DestroyWindow` 或 WINDOWS API `DestroyWindow` 。

- 使用運算子明確刪除 **`delete`** 。

第一個案例是最常見的。 即使您的程式碼不會直接呼叫，也適用此案例 `DestroyWindow` 。 當使用者直接關閉框架視窗時，此動作會產生 WM_CLOSE 訊息，而此訊息的預設回應會在 `DestroyWindow.` 父視窗終結時呼叫，而 Windows 會呼叫 `DestroyWindow` 其所有子系。

第二種情況是，在 **`delete`** Windows 物件上使用運算子的情況應該很罕見。 在某些情況下，使用 **`delete`** 是正確的選擇。

## <a name="auto-cleanup-with-cwndpostncdestroy"></a>使用 CWnd 自動清除：:P ostNcDestroy

當系統終結 Windows 視窗時，會 WM_NCDESTROY 最後傳送到該視窗的 Windows 訊息。 `CWnd`該訊息的預設處理常式是[CWnd：： OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy)。 `OnNcDestroy`會 `HWND` 從 c + + 物件卸離，並呼叫虛擬函式 `PostNcDestroy` 。 有些類別會覆寫這個函式，以刪除 c + + 物件。

的預設執行 `CWnd::PostNcDestroy` 不會執行任何操作，這適用于在堆疊框架上配置或內嵌于其他物件中的視窗物件。 這不適用於設計為在堆積上配置的 window 物件，而不需要任何其他物件。 換句話說，它不適合不是內嵌在其他 c + + 物件中的視窗物件。

專供在堆積上單獨配置的類別會覆寫 `PostNcDestroy` 方法來執行**刪除**。 此語句將會釋放與 c + + 物件相關聯的任何記憶體。 雖然預設的 `CWnd` 析構函式會在 `DestroyWindow` *M_HWND*不是 Null 時呼叫，但這不會導致無限遞迴，因為在清除階段會中斷控制碼和 Null。

> [!NOTE]
> 系統通常會 `CWnd::PostNcDestroy` 在處理 Windows WM_NCDESTROY 訊息，且 `HWND` 不再連接和 c + + 視窗物件時呼叫。 如果發生失敗，系統也會 `CWnd::PostNcDestroy` 在最多[CWnd：： Create](../mfc/reference/cwnd-class.md#create)呼叫的執行中呼叫。 本主題稍後將說明自動清除規則。

## <a name="auto-cleanup-classes"></a>自動清除類別

下列類別不是為了自動清除而設計的。 它們通常會內嵌在其他 c + + 物件或堆疊上：

- 所有標準 Windows 控制項（ `CStatic` 、 `CEdit` 、 `CListBox` 等）。

- 直接從衍生的任何子視窗 `CWnd` （例如，自訂控制項）。

- 分隔視窗（ `CSplitterWnd` ）。

- 預設控制列（衍生自的類別 `CControlBar` ，請參閱[技術提示 31](../mfc/tn031-control-bars.md) ，以啟用控制列物件的自動刪除）。

- `CDialog`針對堆疊框架上的強制回應對話方塊所設計的對話方塊（）。

- 以外的所有標準對話方塊 `CFindReplaceDialog` 。

- ClassWizard 所建立的預設對話。

下列類別是針對自動清除而設計的。 它們通常會在堆積上自行配置：

- 主框架視窗（直接或間接衍生自 `CFrameWnd` ）。

- View windows （直接或間接衍生自 `CView` ）。

如果您想要中斷這些規則，您必須覆寫 `PostNcDestroy` 衍生類別中的方法。 若要將自動清除新增至您的類別，請呼叫您的基類，然後執行**刪除此**動作。 若要從您的類別中移除自動清除，請直接呼叫， `CWnd::PostNcDestroy` 而不是 `PostNcDestroy` 直接基類的方法。

變更自動清除行為最常見的用法，就是建立可在堆積上配置的非強制回應對話方塊。

## <a name="when-to-call-delete"></a>呼叫 delete 的時機

我們建議您呼叫 `DestroyWindow` 來摧毀 Windows 物件，也就是 c + + 方法或全域 `DestroyWindow` API。

請勿呼叫全域 `DestroyWindow` API 來摧毀 MDI 子視窗。 您應該改為使用虛擬方法 `CWnd::DestroyWindow` 。

對於不執行自動清除的 c + + 視窗物件， **`delete`** `DestroyWindow` `CWnd::~CWnd` 如果 VTBL 未指向正確衍生的類別，則使用運算子可能會導致記憶體流失。 發生這種情況的原因是系統找不到要呼叫的適當摧毀方法。 使用 `DestroyWindow` 而不是 **`delete`** 避免這些問題。 因為這可能是微妙的錯誤，所以如果您有風險，在 debug 模式下編譯將會產生下列警告。

```
Warning: calling DestroyWindow in CWnd::~CWnd
    OnDestroy or PostNcDestroy in derived class will not be called
```

在執行自動清除的 c + + Windows 物件案例中，您必須呼叫 `DestroyWindow` 。 如果您直接使用 **`delete`** 運算子，MFC 診斷記憶體配置器會通知您釋放記憶體兩次。 這兩個專案是您的第一個明確呼叫，而間接呼叫會在的自動清除執行中**刪除此**專案 `PostNcDestroy` 。

`DestroyWindow`在非自動清除物件上呼叫之後，c + + 物件仍會繼續進行，但*m_hWnd*將會是 Null。 `DestroyWindow`在自動清除物件上呼叫之後，c + + 物件將會消失，並由的自動清除執行中的 c + + delete 運算子釋放 `PostNcDestroy` 。

## <a name="see-also"></a>另請參閱

[依數位的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依類別區分的技術提示](../mfc/technical-notes-by-category.md)

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
ms.openlocfilehash: 9802669468cbbba89f23b8ac127358d1fc15ec9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370415"
---
# <a name="tn017-destroying-window-objects"></a>TN017：終結視窗物件

本說明描述了[CWnd::PostNc銷毀方法](../mfc/reference/cwnd-class.md#postncdestroy)的使用。 如果要對派生物件進行自定義分配,`CWnd`請使用此方法。 此註釋還解釋了為什麼應該使用[CWnd::DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow)銷毀C++ Windows 物件而不是**刪除**運算符。

如果您遵循本主題中的指南,則將幾乎沒有清理問題。 這些問題可能由忘記刪除/釋放C++記憶體、忘記釋放系統資源(如 s)`HWND`或釋放物件的次數過多等問題導致。

## <a name="the-problem"></a>問題

每個視窗物件(派生自`CWnd`的類別)都表示C++物件和 。 `HWND` C++物件在應用程式的堆中分配,`HWND`並且視窗管理器在系統資源中分配。 由於有幾種方法可以銷毀視窗物件,因此我們必須提供一組規則來防止系統資源或記憶體洩漏。 這些規則還必須防止物件和 Windows 句柄被銷毀一次以上。

## <a name="destroying-windows"></a>銷毀視窗

以下是銷毀 Windows 物件的兩種允許方法:

- 呼叫`CWnd::DestroyWindow`或 Windows `DestroyWindow`API 。

- 使用**刪除**運算符顯式刪除。

第一種情況是迄今為止最常見的。 即使您的代碼不直接調用`DestroyWindow`,此情況也適用。 當使用者直接關閉框架視窗時,此操作將生成WM_CLOSE消息,對此消息的預設回應是調用`DestroyWindow.`「當父視窗被銷毀時,Windows 會`DestroyWindow`調用 其所有子級」。

第二種情況是**刪除運算符在**Windows 物件上使用的情況應該很少。 以下是使用**刪除**的正確選擇。

## <a name="auto-cleanup-with-cwndpostncdestroy"></a>使用 CWnd 自動清理::PostNc銷毀

當系統破壞 Windows 視窗時,發送到該視窗的最後一個 Windows 消息將WM_NCDESTROY。 該訊息`CWnd`的預設處理程式是[CWnd::onNc 銷毀](../mfc/reference/cwnd-class.md#onncdestroy)。 `OnNcDestroy`將從C++物件`HWND`分離,並調用虛擬函`PostNcDestroy`數 。 某些類重寫此函數以刪除C++物件。

的`CWnd::PostNcDestroy`默認實現不執行任何操作,這適用於在堆疊框架上分配或嵌入到其他物件中的視窗物件。 這不適用於設計為在堆上分配而不分配任何其他對象的視窗物件。 換句話說,它不適用於未嵌入到其他C++對象的視窗物件。

那些設計為單獨在堆上分配的類別重寫`PostNcDestroy`方法以執行**刪除此**。 此語句將釋放與C++對象關聯的任何記憶體。 即使預設`CWnd`析構函數調`DestroyWindow`用 ,如果*m_hWnd*是非 NULL,這也不會導致無限遞歸,因為句柄將在清理階段分離和 NULL。

> [!NOTE]
> 系統通常在處理`CWnd::PostNcDestroy`Windows WM_NCDESTROY消息後調`HWND`用, 並且 C++視窗物件不再連接。 系統還將調用`CWnd::PostNcDestroy`大多數[CWnd:::如果發生故障,創建](../mfc/reference/cwnd-class.md#create)調用。 本主題稍後將介紹自動清理規則。

## <a name="auto-cleanup-classes"></a>自動清理類

以下類不是為自動清理而設計的。 它們通常嵌入到其他C++物件或堆疊中:

- 所有標準 Windows`CStatic``CEdit``CListBox`控件 (、、等)。

- 直接派生自`CWnd`的任何子視窗(例如,自定義控制項)。

- 分割視窗 (`CSplitterWnd`。

- 默認控制欄(派生自`CControlBar`的類,請參閱[技術說明 31,](../mfc/tn031-control-bars.md)用於啟用控制項列物件的自動刪除)。

- 為堆疊`CDialog`的模式對話框設計的對話框 ( )

- 除`CFindReplaceDialog`之外的所有標準對話方塊。

- 類嚮導創建的默認對話方塊。

以下類專為自動清理而設計。 它們通常由堆上自己分配:

- 主框架視窗(直接或間接派生自`CFrameWnd`)。

- 查看視窗(直接或間接派生自`CView`)。

如果要破壞這些規則,則必須重寫派生類中`PostNcDestroy`的方法。 要向類別新增自動清理,請呼叫基類別,然後刪除**此**。 要從類中刪除自動清理,請直接調用`CWnd::PostNcDestroy`而不是直接基`PostNcDestroy`類 的方法。

更改自動清理行為的最常見用途是創建可在堆上分配的無模式對話方塊。

## <a name="when-to-call-delete"></a>何時呼叫刪除

我們建議您調用`DestroyWindow`以銷毀 Windows 物件,C++`DestroyWindow`方法或全域 API。

不要調用全域`DestroyWindow`API 來銷毀 MDI 子視窗。 您應該改用虛擬方法`CWnd::DestroyWindow`。

對於不執行自動清理的C++視窗物件,如果 VTBL 未指向正確派生的類,則當`DestroyWindow`您嘗試`CWnd::~CWnd`呼叫析構函數時,使用**delete**運算符可能會導致記憶體洩漏。 這是因為系統找不到要調用的適當銷毀方法。 使用`DestroyWindow`而不是**刪除**可以避免這些問題。 由於這可能是一個微妙的錯誤,因此,如果您處於危險之中,在調試模式下編譯將生成以下警告。

```
Warning: calling DestroyWindow in CWnd::~CWnd
    OnDestroy or PostNcDestroy in derived class will not be called
```

如果C++執行自動清理的 Windows 物件,則必須`DestroyWindow`呼叫 。 如果您直接使用**刪除**運算符,MFC 診斷記憶體分配器將通知您釋放記憶體兩次。 這兩個事件是您的第一個顯式呼叫,以及間接呼叫,用於在自動清理實現中刪除`PostNcDestroy`**此呼叫**。

調用`DestroyWindow`非自動清理物件后,C++物件仍將在周圍,但*m_hWnd*將為 NULL。 調用`DestroyWindow`自動清理物件后,C++物件將消失,由C++刪除運算符在 自動清理實現`PostNcDestroy`中 釋放。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)

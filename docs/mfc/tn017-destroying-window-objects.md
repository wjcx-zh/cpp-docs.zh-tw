---
title: TN017： 終結視窗物件 |Microsoft 文件
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
ms.openlocfilehash: c6bba255403d31e7a1fa03febb0c760d20cdc81c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="tn017-destroying-window-objects"></a>TN017：終結視窗物件
此附註將描述使用[CWnd::PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy)方法。 使用這個方法，如果您想要執行的自訂的配置`CWnd`-衍生物件。 此提示也會說明為什麼您應該使用[cwnd:: Destroywindow](../mfc/reference/cwnd-class.md#destroywindow)終結 c + + 視窗物件，而不是`delete`運算子。  
  
 如果您遵循本主題中的指導方針，將會有幾個清除問題。 這些問題造成的問題，例如忘記刪除/釋放 c + + 的記憶體，忘記釋放系統資源，例如`HWND`s，或釋放物件太多次。  
  
## <a name="the-problem"></a>問題  
 每個 windows 物件 (物件類別的衍生自`CWnd`) 表示 c + + 物件和`HWND`。 C + + 物件會在應用程式的堆積中配置和`HWND`s 會配置視窗管理員中的系統資源。 由於有數種方式可終結視窗物件，我們必須提供一組規則，導致系統資源或記憶體流失。 這些規則也必須防止物件和 Windows 控制代碼被終結一次以上。  
  
## <a name="destroying-windows"></a>終結視窗  
 終結視窗物件的兩個允許的方式如下：  
  
-   呼叫`CWnd::DestroyWindow`或 Windows API `DestroyWindow`。  
  
-   使用明確刪除`delete`運算子。  
  
 第一個案例中是最常見到目前為止。 此案例適用於，即使您的程式碼不會呼叫`DestroyWindow`直接。 當使用者直接關閉框架視窗時，這個動作會產生`WM_CLOSE`訊息，以及預設回應這個訊息是呼叫`DestroyWindow.`父視窗終結時，Windows 會呼叫`DestroyWindow`的所有子系。  
  
 第二個案例中，使用`delete`運算子，在 Windows 物件應該很少見。 下列為某些情況下使用`delete`是正確的選擇。  
  
## <a name="auto-cleanup-with-cwndpostncdestroy"></a>與 CWnd::PostNcDestroy 自動清除  
 系統會終結 Windows 視窗，最後一個 Windows 訊息傳送至視窗時， `WM_NCDESTROY`。 預設值`CWnd`該訊息的處理常式是[cwnd::](../mfc/reference/cwnd-class.md#onncdestroy)。 `OnNcDestroy` 將卸離`HWND`從 c + + 物件，並且呼叫虛擬函式`PostNcDestroy`。 某些類別覆寫這個函式來刪除 c + + 物件。  
  
 預設實作`CWnd::PostNcDestroy`不做任何動作，這是適當的堆疊框架上配置或其他物件中內嵌的視窗物件。 這不設計成可在不含任何其他物件在堆積上配置的視窗物件的適當。 換句話說，它不適用於不會內嵌在其他 c + + 物件的視窗物件。  
  
 這些設計來單獨在堆積上配置的類別覆寫`PostNcDestroy`方法，以執行`delete this`。 這個陳述式會釋放任何與 c + + 物件相關聯的記憶體。 即使預設`CWnd`解構函式呼叫`DestroyWindow`如果`m_hWnd`是不是 NULL，這不會導致無限遞迴因為控制代碼時，將會中斷連結和 NULL 清除階段。  
  
> [!NOTE]
>  系統通常會呼叫`CWnd::PostNcDestroy`處理 Windows 之後`WM_NCDESTROY`訊息和`HWND`和 c + + 視窗物件已經沒有連線。 系統也會呼叫`CWnd::PostNcDestroy`實作中的大部分[cwnd:: Create](../mfc/reference/cwnd-class.md#create)發生失敗時呼叫。 自動清除規則會在本主題稍後所述。  
  
## <a name="auto-cleanup-classes"></a>自動清除類別  
 下列類別的設計不會自動清除。 它們通常被內嵌在其他 c + + 物件，或在堆疊上：  
  
-   所有標準 Windows 控制項 (`CStatic`， `CEdit`，`CListBox`等等)。  
  
-   任何子視窗直接衍生自`CWnd`（例如，自訂控制項）。  
  
-   分隔視窗 (`CSplitterWnd`)。  
  
-   預設控制列 (類別衍生自`CControlBar`，請參閱[技術提示 31](../mfc/tn031-control-bars.md)啟用自動刪除控制列物件)。  
  
-   對話方塊 (`CDialog`) 堆疊框架上的強制回應對話方塊的設計。  
  
-   所有標準都對話方塊除了`CFindReplaceDialog`。  
  
-   類別精靈所建立的預設對話方塊。  
  
 下列類別被設計為自動清除。 它們通常是在堆積上配置本身：  
  
-   主框架視窗 (直接或間接衍生自`CFrameWnd`)。  
  
-   檢視 windows (直接或間接衍生自`CView`)。  
  
 如果您想要中斷這些規則，您必須覆寫`PostNcDestroy`衍生類別中的方法。 若要將自動清除加入至類別，呼叫基底類別，然後執行`delete this`。 若要從您的類別中移除自動清除，請呼叫`CWnd::PostNcDestroy`直接而不是`PostNcDestroy`直接基底類別方法。  
  
 變更自動清除行為的常見用法是在堆積上建立非強制回應對話方塊，可配置。  
  
## <a name="when-to-call-delete"></a>時要呼叫刪除  
 我們建議您呼叫`DestroyWindow`終結視窗物件，在 c + + 方法或全域`DestroyWindow`應用程式開發介面。  
  
 不會呼叫全域`DestroyWindow`終結 MDI 子視窗的應用程式開發介面。 您應該使用的虛擬方法`CWnd::DestroyWindow`改為。  
  
 使用 c + + 視窗物件，不會執行自動清除，`delete`運算子可能會導致記憶體流失，當您嘗試呼叫`DestroyWindow`中`CWnd::~CWnd`如果 VTBL 未指向正確的衍生類別的解構函式。 這是因為系統找不到適當的損毀要呼叫方法。 使用`DestroyWindow`而不是`delete`可避免這些問題。 因為這可能會難以察覺的錯誤，在偵錯模式中編譯會產生下列警告您是否有風險。  
  
```  
Warning: calling DestroyWindow in CWnd::~CWnd  
    OnDestroy or PostNcDestroy in derived class will not be called  
```  
  
 在執行自動清除的 c + + 視窗物件，您必須呼叫`DestroyWindow`。 如果您使用`delete`運算子直接，MFC 診斷記憶體配置器會通知您，您會釋放記憶體兩次。 兩個項目是您第一次的明確呼叫和間接呼叫`delete this`自動清除實作`PostNcDestroy`。  
  
 在呼叫`DestroyWindow`非自動清除物件上的 c + + 物件仍會但`m_hWnd`會是 NULL。 在呼叫`DestroyWindow`自動清除物件上的 c + + 物件就會消失，由 c + + delete 運算子中的自動清除實作釋放`PostNcDestroy`。  
  
## <a name="see-also"></a>另請參閱  
 [依數字的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)


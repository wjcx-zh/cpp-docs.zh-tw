---
title: "TN017：終結視窗物件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.objects"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "終結視窗"
  - "PostNcDestroy 方法"
  - "TN017"
ms.assetid: 5bf208a5-5683-439b-92a1-547c5ded26cd
caps.latest.revision: 15
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN017：終結視窗物件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個會描述 [CWnd::PostNcDestroy](../Topic/CWnd::PostNcDestroy.md) 方法的用法。  如果您要做 `CWnd` 衍生物件的自訂配置，請使用這個方法。  這個附註也說明為何應該使用 [CWnd::DestroyWindow](../Topic/CWnd::DestroyWindow.md) 終結 C \+\+ 視窗物件而非 `delete` 運算子。  
  
 如果您遵循本主題中的方針，您將會有少量清除的問題。  這些問題可能造成問題 \(例如多次忘記刪除\/釋放 C\+\+ 記憶體，忘記釋放像 `HWND`的系統資源或釋放物件。  
  
## 問題  
 每個視窗物件 \(衍生自 `CWnd`之類別的物件\) 表示兩個 C \+\+. 物件和 `HWND`。  C\+\+ 物件由視窗管理員在應用程式堆積中配置，而 `HWND`在系統資源配置。  由於有幾個方式終結視窗物件，我們必須提供防止系統資源或記憶體遺漏的規則集。  這些規則也必須防止物件與視窗控制代碼終結一次以上。  
  
## 終結視窗  
 以下是兩個允許的方式終結視窗物件：  
  
-   呼叫 `CWnd::DestroyWindow` 或 Windows 應用程式開發介面 `DestroyWindow`。  
  
-   使用 `delete` 運算子明確刪除。  
  
 第一種情況很明顯是最常見的。  這種情況，即使您的程式碼不會直接呼叫 `DestroyWindow` 。  當使用者直接關閉視窗框架時，這個動作會產生 `WM_CLOSE` 訊息，而當終結父視窗時，與此訊息相關聯的預設回應是呼叫 `DestroyWindow.` ，視窗呼叫所有子系的 `DestroyWindow` 。  
  
 第二種情況下，使用 Windows 的 `delete` 運算子物件，應該很罕見。  下列是使用 `delete` 的一些情況是正確的選擇。  
  
## 使用 CWnd::PostNcDestroy 自動清除  
 當系統會終結視窗視窗時，最後一個視窗訊息傳送給視窗是 `WM_NCDESTROY`。  該訊息的預設 `CWnd` 處理常式是 [CWnd::OnNcDestroy](../Topic/CWnd::OnNcDestroy.md)。  `OnNcDestroy` 會從 C\+\+ 物件中斷 `HWND` 並呼叫虛擬函式 `PostNcDestroy`。  某些類別覆寫這個函式來刪除 C\+\+ 物件。  
  
 `CWnd::PostNcDestroy` 的預設實作沒有任何作用，為 Windows 物件適合用在堆疊框架在其他物件配置或內嵌。  對於在設計上在堆積上配置而不需要任何其他物件的視窗物件並不適當。  換句話說，未內嵌在其他 C\+\+ 物件的視窗物件不是適當的。  
  
 設計上在堆積中個別配置覆寫 `PostNcDestroy` 方法來執行 `delete this` 的類別。  這個陳述式會釋放所有與 C\+\+ 物件相關的記憶體。  即使預設 `CWnd` 解構函式呼叫 `DestroyWindow` ，如果 `m_hWnd` 為非 null，這不會導致無限遞迴，因為控制代碼在清除階段期間將會中斷連接和空白。  
  
> [!NOTE]
>  系統通常會呼叫 `CWnd::PostNcDestroy` ，在處理 Windows `WM_NCDESTROY` 訊息後，而 `HWND` 和 C\+\+ Windows 物件不再連接。  如果失敗，系統也會呼叫在大部分 [CWnd::Create](../Topic/CWnd::Create.md) 呼叫之實作的 `CWnd::PostNcDestroy` 。  自動清除規則在此主題中稍後說明。  
  
## 自動清除類別  
 下列類別不會自動清除設計。  它們通常是內嵌於其他 C\+\+ 物件或堆疊上：  
  
-   所有標準 Windows 控制項 \(`CStatic`、 `CEdit`、`CListBox`，依此類推\)。  
  
-   直接衍生自 `CWnd` 的任何子視窗 \(例如，自訂控制項\)。  
  
-   分隔視窗\(`CSplitterWnd`\)。  
  
-   預設的控制列 \(衍生自 `CControlBar`的類別，啟用控制列物件的自動刪除請參閱 [Technical Note 31](../mfc/tn031-control-bars.md) \)。  
  
-   為在堆疊框架的強制回應對話方塊 \(`CDialog`\) 設計的對話方塊。  
  
-   所有標準對話方塊除了 `CFindReplaceDialog` 之外。  
  
-   ClassWizard 建立的預設對話方塊。  
  
 下列類別不會自動清除設計。  它們在堆積本身通常會指派：  
  
-   主框架視窗 \(直接或間接衍生自 `CFrameWnd`\)。  
  
-   檢視視窗 \(直接或間接衍生自 `CView`\)。  
  
 如果您要違反這些規則矩陣，您必須覆寫您的衍生類別的 `PostNcDestroy` 方法。  若要將自動清除加入倒您的類別，呼叫您的基底類別然後執行 `delete this`。  從您的類別要取消自動清除，請直接呼叫 `CWnd::PostNcDestroy` 而不是您的直接基底類別 `PostNcDestroy` 方法。  
  
 最常見的變更自動清除行為是建立在堆積上配置的非強制回應對話方塊。  
  
## 何時呼叫 Delete：  
 我們建議您呼叫 `DestroyWindow` 終結視窗物件， C\+\+ 方法或全域 `DestroyWindow` 應用程式開發介面。  
  
 不要呼叫全域 `DestroyWindow` API 終結 MDI 子視窗。  應改用虛擬方法 `CWnd::DestroyWindow`。  
  
 如果 VTBL 不正確指向衍生類別，當您嘗試在 `CWnd::~CWnd` 解構函式呼叫 `DestroyWindow` 時，對於 C\+\+ 不執行自動清除的視窗物件，使用 `delete` 運算子會造成記憶體遺漏 \(Memory Leak\)。  因為系統無法終結方法的適當呼叫，就會發生這種情況。  使用 `delete` 而不是 `DestroyWindow` 避免這些問題。  由於在偵錯模式這是一個小錯誤，因此如果您具有風險將會產生下列警告。  
  
```  
Warning: calling DestroyWindow in CWnd::~CWnd  
   OnDestroy or PostNcDestroy in derived class will not be called  
```  
  
 在 C\+\+ 執行自動清除的視窗物件，您必須呼叫 `DestroyWindow`。  如果直接使用 `delete` 運算子， MFC 診斷記憶體配置器會通知您釋放記憶體兩次。  兩個事件是您的第一個明確和間接在 `PostNcDestroy`的自動清除實作對 `delete this` 的呼叫。  
  
 呼叫在非自動清除物件的 `DestroyWindow` 之後， C\+\+ 物件還會存在，但 `m_hWnd` 會是 null。  呼叫在自動清除物件的 `DestroyWindow` 之後， C\+\+ 物件將消失，由 `PostNcDestroy`的自動清除實作的 C\+\+ delete 運算子釋放。  
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)
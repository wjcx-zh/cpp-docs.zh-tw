---
title: TN025：文件、檢視和框架建立
ms.date: 11/04/2016
f1_keywords:
- vc.creation
helpviewer_keywords:
- documents [MFC], view and frame creation
- TN025
ms.assetid: 09254d72-6e1d-43db-80e9-693887dbeda2
ms.openlocfilehash: aa8bc305848ce95e0b5bfef1ac6785b18bc84015
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50634755"
---
# <a name="tn025-document-view-and-frame-creation"></a>TN025：文件、檢視和框架建立

> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

本附註將描述建立 WinApps、DocTemplate、文件、框架和檢視及其擁有權的問題。

## <a name="winapp"></a>WinApp

系統中有一個 `CWinApp` 物件。

該物件是由架構的內部實作 `WinMain` 以靜態方式建構並初始化。 您必須衍生自`CWinApp`才能執行有用 (例外狀況： MFC 擴充 Dll 不應有`CWinApp`執行個體 — 進行初始化`DllMain`改為)。

一個 `CWinApp` 物件會擁有一份文件範本的清單 (`CPtrList`)。 每個應用程式會有一個或多個文件範本。 DocTemplate 通常是從 `CWinApp::InitInstance` 中的資源檔 (也就是字串陣列) 載入。

```
pTemplate = new CDocTemplate(IDR_MYDOCUMENT, ...);

AddDocTemplate(pTemplate);
```

這一個 `CWinApp` 物件會擁有應用程式中的所有框架視窗。 應用程式的主框架視窗應儲存在`CWinApp::m_pMainWnd`; 您的設定通常*m_pMainWnd*在`InitInstance`如果您有 appwizard 未替您的實作。 若是單一文件介面 (SDI)，這個 `CFrameWnd` 就會做為主應用程式框架視窗，也是唯一的文件框架視窗。 若是多重文件介面 (MDI)，這會是 MDI 框架 (`CMDIFrameWnd` 類別)，它會做為主應用程式框架視窗並且包含所有子 `CFrameWnd`。 每個子視窗都屬於 `CMDIChildWnd` 類別 (衍生自 `CFrameWnd`)，並且做為可能有多個文件框架視窗的其中一個。

## <a name="doctemplates"></a>DocTemplate

`CDocTemplate` 是文件的建立者與管理者。 它擁有本身所建立的文件。 如果您的應用程式使用下面所述的資源架構方法，就不需要衍生自 `CDocTemplate`。

若是 SDI 應用程式，`CSingleDocTemplate` 類別會追蹤一份開啟的文件。 若是 MDI 應用程式，`CMultiDocTemplate` 類別會保留一份所有從該範本建立且目前開啟之文件的清單 (`CPtrList`)。 `CDocTemplate::AddDocument` 和 `CDocTemplate::RemoveDocument` 會提供虛擬成員函式，用來在範本中加入或移除文件。 `CDocTemplate` 是的 friend`CDocument`讓我們能夠以受保護的方式設定`CDocument::m_pDocTemplate`的返回指標設回指向建立文件的文件範本。

`CWinApp` 會處理預設的 `OnFileOpen` 實作，接著該實作就會查詢所有文件範本。 實作中包含尋找已開啟的文件，以及決定採用何種格式開啟新文件。

`CDocTemplate` 會管理文件和框架的 UI 繫結。

`CDocTemplate` 會保留未命名文件數目的計數。

## <a name="cdocument"></a>CDocument

A`CDocument`擁有者`CDocTemplate`。

文件會有一份目前正在檢視文件之已開啟檢視 (衍生自 `CView`) 的清單 (`CPtrList`)。

文件不會建立/終結檢視，不過它們會在建立之後互相連接。 當文件關閉時 (透過 [檔案]/[關閉])，所有連接的檢視都會關閉。 當文件中的最後一個檢視關閉時 (透過 [視窗]/[關閉])，文件將會關閉。

`CDocument::AddView`、`RemoveView` 介面可用來維護檢視清單。 `CDocument` 是的 friend`CView`因此我們可以設定`CView::m_pDocument`返回指標。

## <a name="cframewnd"></a>CFrameWnd

`CFrameWnd` (也稱為框架) 的功能與在 MFC 1.0 中相同，不過，`CFrameWnd` 類別現在設計為可在多種情況下使用，而不需衍生新的類別。 衍生的類別 `CMDIFrameWnd` 和 `CMDIChildWnd` 也會經過強化，當中便已實作許多標準命令。

`CFrameWnd` 負責在框架工作區中建立視窗。 通常框架工作區中會填入一個主視窗。

若是 MDI 框架視窗，工作區中會填入 MDICLIENT 控制項，該控制項會是所有 MDI 子框架視窗的父項。 若是 SDI 框架視窗或 MDI 子框架視窗，工作區中通常會填入 `CView` 衍生的視窗物件。 若是使用 `CSplitterWnd`，檢視的工作區中會填入 `CSplitterWnd` 視窗物件，而 `CView` 衍生的視窗物件 (每分割窗格有一個物件) 會建立為 `CSplitterWnd` 的子視窗。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)


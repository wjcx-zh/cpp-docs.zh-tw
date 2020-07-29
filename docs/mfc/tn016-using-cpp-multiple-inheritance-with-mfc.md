---
title: TN016：搭配使用 C++多重繼承與 MFC
ms.date: 06/28/2018
f1_keywords:
- vc.inheritance
helpviewer_keywords:
- TN016
- MI (Multiple Inheritance)
- multiple inheritance, MFC support for
ms.assetid: 4ee27ae1-1410-43a5-b111-b6af9b84535d
ms.openlocfilehash: c44639e713f6d0b26d5b74e9f645f60c8627e0c8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231763"
---
# <a name="tn016-using-c-multiple-inheritance-with-mfc"></a>TN016：搭配使用 C++多重繼承與 MFC

此提示說明如何對於 Microsoft Foundation Classes 搭配使用多重繼承 (MI)。 使用 MI 不需要 MFC。 MI 未使用於任何 MFC 類別，並且不需要撰寫類別庫。

以下副標題說明 MI 如何影響一般 MFC 慣例的使用並且涵蓋一些 MI 的限制。 其中一些限制為一般 C++ 限制。 其他則是 MFC 結構加上的限制。

在本技術提示結尾，您可找到使用 MI 的完整 MFC 應用程式。

## <a name="cruntimeclass"></a>CRuntimeClass

MFC 的持續性和動態物件建立機制會使用[CRuntimeClass](../mfc/reference/cruntimeclass-structure.md)資料結構來唯一識別類別。 MFC 會在應用程式中將這些結構之一與各個動態和/或可序列化類別關聯。 當應用程式透過使用 `AFX_CLASSINIT` 類別的特殊靜態物件啟動時，會將這些結構初始化。

目前的 `CRuntimeClass` 實作不支援 MI 執行階段類型資訊。 這並不表示您在 MFC 應用程式中無法使用 MI。 不過，您在使用具有一個以上的基底類別的物件時，您會有一些責任。

如果物件有多個基類， [CObject：： IsKindOf](../mfc/reference/cobject-class.md#iskindof)方法將不會正確判斷其類型。 因此，您無法使用[cobject](../mfc/reference/cobject-class.md)作為虛擬基類，而且所有對成員函式的呼叫 `CObject` （例如[cobject：：序列化](../mfc/reference/cobject-class.md#serialize)和[cobject：： operator new](../mfc/reference/cobject-class.md#operator_new) ）都必須具有範圍限定詞，讓 c + + 能夠區分適當的函式呼叫。 當程式在 MFC 中使用 MI 時，包含 `CObject` 基底類別的類別必須是在基底類別清單中最左邊的類別。

替代方式是使用 **`dynamic_cast`** 運算子。 使用 MI 將物件轉換為其基底類別之一，會強制編譯器使用所提供的基底類別中的函式。 如需詳細資訊，請參閱[Dynamic_cast 運算子](../cpp/dynamic-cast-operator.md)。

## <a name="cobject---the-root-of-all-classes"></a>CObject - 所有類別的根。

所有重要類別都是直接或間接從類別 `CObject` 衍生。 `CObject` 並沒有任何成員資料，不過它確實有一些預設功能。 當您使用 MI 時，通常會從兩個或多個 `CObject` 衍生類別繼承。 下列範例說明類別可以如何繼承自[CFrameWnd](../mfc/reference/cframewnd-class.md)和[CObList](../mfc/reference/coblist-class.md)：

```cpp
class CListWnd : public CFrameWnd, public CObList
{
    // ...
};
CListWnd myListWnd;
```

在此情況下，會包含 `CObject` 兩次。 這表示您需要一個方法使 `CObject` 方法或運算子的所有參考意義清楚。 **Operator new**和[運算子 delete](../mfc/reference/cobject-class.md#operator_delete)是必須區分的兩個運算子。 做為另一個範例，下列程式碼會在編譯期間造成錯誤：

```cpp
myListWnd.Dump(afxDump); // compile time error, CFrameWnd::Dump or CObList::Dump
```

## <a name="reimplementing-cobject-methods"></a>重新實作 CObject 方法

當您建立具有兩個或多個 `CObject` 衍生的基底類別的新類別時，您應該實作要其他人使用的 `CObject` 方法。 運算子 **`new`** 和 **`delete`** 是強制性[的](../mfc/reference/cobject-class.md#dump)，建議使用傾印。 下列範例會實作 **`new`** 和 **`delete`** 運算子和 `Dump` 方法：

```cpp
class CListWnd : public CFrameWnd, public CObList
{
public:
    void* operator new(size_t nSize)
    {
        return CFrameWnd:: operator new(nSize);
    }
    void operator delete(void* p)
    {
        CFrameWnd:: operator delete(p);
    }
    void Dump(CDumpContent& dc)
    {
        CFrameWnd::Dump(dc);
        CObList::Dump(dc);
    }
    // ...
};
```

## <a name="virtual-inheritance-of-cobject"></a>CObject 的虛擬繼承

看起來也許虛擬繼承 `CObject` 函式會解決函式模稜兩可的問題，不過實際並不是這樣。 因為 `CObject` 中沒有成員資料，所以您並不需要虛擬繼承來防止產生基底類別成員資料的多個複本。 在稍早顯示的第一個範例中，`Dump` 虛擬方法仍然模稜兩可，因為它在 `CFrameWnd` 和 `CObList` 中的實作不一樣。 去除模稜兩可的最佳方式是遵照上一節所提出的建議。

## <a name="cobjectiskindof-and-run-time-typing"></a>CObject::IsKindOf 和執行階段類型

中的 MFC 所支援的執行時間類型機制會 `CObject` 使用宏 DECLARE_DYNAMIC、IMPLEMENT_DYNAMIC、DECLARE_DYNCREATE、IMPLEMENT_DYNCREATE、DECLARE_SERIAL 和 IMPLEMENT_SERIAL。 這些巨集可執行執行階段類型檢查，以保證安全向下轉型。

這些巨集只支援單一基底類別，並且會對多重繼承的類別以限定的方式執行。 您在 IMPLEMENT_DYNAMIC 或 IMPLEMENT_SERIAL 中指定的基類應該是第一個（或最左邊的）基類。 這個位置可讓您只針對最左邊的基底類別進行類型檢查。 執行階段類型系統對於其他基底類別毫無所知。 在下列範例中，執行階段系統會對 `CFrameWnd` 進行類型檢查，但是對於 `CObList` 毫無所知。

```cpp
class CListWnd : public CFrameWnd, public CObList
{
    DECLARE_DYNAMIC(CListWnd)
    // ...
};
IMPLEMENT_DYNAMIC(CListWnd, CFrameWnd)
```

## <a name="cwnd-and-message-maps"></a>CWnd 和訊息對應

若要讓 MFC 訊息對應系統正確運作，有兩項額外需求：

- 只能有一個 `CWnd` 衍生的基底類別。

- `CWnd` 衍生的基底類別必須是第一個 (或最左邊的) 基底類別。

以下一些不會運作的範例：

```cpp
class CTwoWindows : public CFrameWnd, public CEdit
{ /* ... */ }; // error : two copies of CWnd

class CListEdit : public CObList, public CEdit
{ /* ... */ }; // error : CEdit (derived from CWnd) must be first
```

## <a name="a-sample-program-using-mi"></a>使用 MI 的範例程式

下列範例是一個獨立應用程式，其中包含一個衍生自 `CFrameWnd` 和[CWinApp](../mfc/reference/cwinapp-class.md)的類別。 我們不建議您以此方式建構應用程式，不過這是具有一個類別的最小 MFC 應用程式的範例。

```cpp
#include <afxwin.h>

class CHelloAppAndFrame : public CFrameWnd, public CWinApp
{
public:
    CHelloAppAndFrame() {}

    // Necessary because of MI disambiguity
    void* operator new(size_t nSize)
        { return CFrameWnd::operator new(nSize); }
    void operator delete(void* p)
        { CFrameWnd::operator delete(p); }

    // Implementation
    // CWinApp overrides
    virtual BOOL InitInstance();
    // CFrameWnd overrides
    virtual void PostNcDestroy();
    afx_msg void OnPaint();

    DECLARE_MESSAGE_MAP()
};

BEGIN_MESSAGE_MAP(CHelloAppAndFrame, CFrameWnd)
    ON_WM_PAINT()
END_MESSAGE_MAP()

// because the frame window is not allocated on the heap, we must
// override PostNCDestroy not to delete the frame object
void CHelloAppAndFrame::PostNcDestroy()
{
    // do nothing (do not call base class)
}

void CHelloAppAndFrame::OnPaint()
{
    CPaintDC dc(this);
    CRect rect;
    GetClientRect(rect);

    CString s = "Hello, Windows!";
    dc.SetTextAlign(TA_BASELINE | TA_CENTER);
    dc.SetTextColor(::GetSysColor(COLOR_WINDOWTEXT));
    dc.SetBkMode(TRANSPARENT);
    dc.TextOut(rect.right / 2, rect.bottom / 2, s);
}

// Application initialization
BOOL CHelloAppAndFrame::InitInstance()
{
    // first create the main frame
    if (!CFrameWnd::Create(NULL, "Multiple Inheritance Sample",
        WS_OVERLAPPEDWINDOW, rectDefault))
        return FALSE;

    // the application object is also a frame window
    m_pMainWnd = this;
    ShowWindow(m_nCmdShow);
    return TRUE;
}

CHelloAppAndFrame theHelloAppAndFrame;
```

## <a name="see-also"></a>另請參閱

[依數位的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依類別區分的技術提示](../mfc/technical-notes-by-category.md)

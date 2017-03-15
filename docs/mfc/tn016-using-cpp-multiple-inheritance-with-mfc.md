---
title: "TN016：搭配使用 C++多重繼承與 MFC | Microsoft Docs"
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
  - "vc.inheritance"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MI (多重繼承)"
  - "多重繼承, 的 MFC 支援"
  - "TN016"
ms.assetid: 4ee27ae1-1410-43a5-b111-b6af9b84535d
caps.latest.revision: 22
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN016：搭配使用 C++多重繼承與 MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個會描述如何使用 Microsoft Foundation Class 的多重繼承 \(MI\)。  使用 MI 不需要與 MFC。  MI 未使用於任何 MFC 類別而不需要撰寫類別庫。  
  
 下列的子主題描述 MI 如何影響使用一般 MFC 慣例以及包含某些 MI 的限制。  其中一些限制為一般 C\+\+ 限制。  MFC 結構加上其他。  
  
 在這個技術提示結束時就會對使用 MI 的完整 MFC 應用程式。  
  
## CRuntimeClass  
 MFC 持續性和動態物件建立機制使用 [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) 資料結構唯一識別類別。  MFC 使這些結構是在應用程式的各個和\/或序列化類別。  當應用程式啟動使用 `AFX_CLASSINIT`型別時，特殊靜態物件這些結構初始化。  
  
 `CRuntimeClass` 的目前實作不支援 MI 執行階段型別資訊。  這並不表示您在 MFC 應用程式無法使用 MI。  然而，您會有某些責任，當您使用具有一個以上的基底類別 \(Base Class\) 的物件一起使用。  
  
 [CObject::IsKindOf](../Topic/CObject::IsKindOf.md) 方法不會正確地判斷物件的型別 \(如果有多個基底類別。  因此，您不能使用 [CObject](../mfc/reference/cobject-class.md) 做為虛擬基底類別，因此，對 `CObject` 成員函式 \(例如 [CObject::Serialize](../Topic/CObject::Serialize.md) 和 [CObject::operator new](../Topic/CObject::operator%20new.md) 的所有呼叫都必須有範圍限定詞，以便 C\+\+ 可以區分適當的函式呼叫。  當程式在 MFC 中的 MI，包含 `CObject` 基底類別的類別必須是在基底類別清單中最左邊的類別。  
  
 使用 `dynamic_cast` 的替代方式是使用 \+\= 運算子。  轉換為與 MI 至其中一個基底類別所提供的基底類別會強制編譯器使用函式。  如需詳細資訊，請參閱[dynamic\_cast 運算子](../cpp/dynamic-cast-operator.md)。  
  
## CObject \-所有類別。  
 任何重要類別是 `CObject`直接或間接衍生。  `CObject` 沒有任何成員資料，不過，它有一些預設功能。  當您使用 MI，將兩個或多個 `CObject`衍生類別通常會繼承。  下列範例示範類別如何從 [CFrameWnd](../mfc/reference/cframewnd-class.md) 和 [CObList](../mfc/reference/coblist-class.md)繼承:  
  
```  
class CListWnd : public CFrameWnd, public CObList  
{  
 ...  
};  
CListWnd myListWnd;  
```  
  
 在此情況下 `CObject` 所包含的兩倍。  這表示您需要區分對 `CObject` 方法或運算子的所有參考。  `operator new` 和 [運算子刪除](../Topic/CObject::operator%20delete.md) 是必須被明確指出的兩個運算子。  做為另一個範例，下列程式碼會產生錯誤在編譯時間:  
  
```  
myListWnd.Dump(afxDump);  
    // compile time error, CFrameWnd::Dump or CObList::Dump ?  
```  
  
## Reimplementing CObject 方法  
 當您建立具有兩個或更多個 `CObject` 衍生的基底類別 \(Base Class\) 的新類別時，您應該實作 `CObject` 方法要其他人使用。  運算子 `new` 和 `delete` 是必須的，建議是使用 [傾印](../Topic/CObject::Dump.md) 。  下列範例建立混合 `new` 及 `delete` 運算子和 `Dump` 方法:  
  
```  
class CListWnd : public CFrameWnd, public CObList  
{  
public:  
    void* operator new(size_t nSize)  
        { return CFrameWnd::operator new(nSize); }  
    void operator delete(void* p)  
        { CFrameWnd::operator delete(p); }  
  
    void Dump(CDumpContent& dc)  
        { CFrameWnd::Dump(dc);  
          CObList::Dump(dc); }  
     ...  
};  
```  
  
## CObject 虛擬繼承  
 看起來虛擬繼承 `CObject` 函式將解決模稜兩可的問題，不過，這並不是這樣。  由於 `CObject`中沒有成員資料，您不需要虛擬繼承防止基底類別成員資料的多個複本。  在顯示之前的第一個範例中， `Dump` 虛擬方法模稜兩可，因為它在 `CFrameWnd` 和 `CObList`以不同的方式實作。  最好的方式移除模稜兩可會遵照上一節顯示的建議。  
  
## CObject::IsKindOf 和執行階段型別  
 在 `CObject` 的 MFC 支援之執行階段的輸入機制使用巨集 `DECLARE_DYNAMIC`、 `IMPLEMENT_DYNAMIC`、 `DECLARE_DYNCREATE`、 `IMPLEMENT_DYNCREATE`、 `DECLARE_SERIAL` 和 `IMPLEMENT_SERIAL`。  這些巨集可執行的執行階段型別檢查以確定安全向下轉型。  
  
 這些巨集只支援單一基底類別，然後將以多重繼承的類別以限定的方式。  您可以在 `IMPLEMENT_DYNAMIC` 指定的基底類別或 `IMPLEMENT_SERIAL` 應該是第一個 \(或最左邊\) 的基底類別。  這將會使您進行型別檢查只最左邊的基底類別。  這個執行階段型別則系統不會知道其他基底類別。  在下列範例中， Runtime 系統就不會進行型別檢查物件，則為 `CFrameWnd`，但是知道 `CObList`。  
  
```  
class CListWnd : public CFrameWnd, public CObList  
{  
    DECLARE_DYNAMIC(CListWnd)  
    ...  
};  
IMPLEMENT_DYNAMIC(CListWnd, CFrameWnd)  
```  
  
## CWnd 和訊息對應  
 若要正確運作 MFC 訊息對應的系統中，有兩個額外的要求:  
  
-   只能有一個 `CWnd`衍生的基底類別。  
  
-   `CWnd`衍生的基底類別必須是第一個 \(或最左邊\) 的基底類別。  
  
 這不會運作的範例:  
  
```  
class CTwoWindows : public CFrameWnd, public CEdit  
    { ... };  
        // error : two copies of CWnd  
  
class CListEdit : public CObList, public CEdit  
    { ... };  
        // error : CEdit (derived from CWnd) must be first  
```  
  
## 使用 MI 的一個範例程式  
 下列範例是由 `CFrameWnd` 和衍生自 [CWinApp](../mfc/reference/cwinapp-class.md)的類別的獨立應用程式。  我們不建議您這樣建構一個應用程式，不過，這是具有類別最小的 MFC 應用程式的範例。  
  
```  
#include <afxwin.h>  
  
class CHelloAppAndFrame : public CFrameWnd, public CWinApp  
{   
public:  
    CHelloAppAndFrame()  
        { }  
  
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
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)
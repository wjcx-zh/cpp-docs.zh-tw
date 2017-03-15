---
title: "TN038：MFC/OLE IUnknown 實作 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.ole"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "彙總巨集 [C++]"
  - "BEGIN_INTERFACE_MAP 巨集"
  - "BEGIN_INTERFACE_PART 巨集"
  - "COM 介面, 基底介面"
  - "DECLARE_INTERFACE_MAP 巨集"
  - "END_INTERFACE_MAP 巨集"
  - "END_INTERFACE_PART 巨集"
  - "INTERFACE_PART 巨集"
  - "IUnknown 介面"
  - "METHOD_PROLOGUE 巨集"
  - "OLE [C++], 實作 IUnknown 介面"
  - "STDMETHOD 巨集"
  - "TN038"
ms.assetid: 19d946ba-beaf-4881-85c6-0b598d7f6f11
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# TN038：MFC/OLE IUnknown 實作
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。  因此，有些程序和主題可能已過期或不正確。  如需最新資訊，建議您在線上文件索引中搜尋相關的主題。  
  
 OLE 2 的核心是「OLE 元件物件模型」或 COM。  COM 會定義合作物件如何彼此通訊的標準。  這包括「物件」外觀的詳細資料，包括如何在物件上分派方法。  COM 也會定義所有 COM 相容類別從其中衍生的基底類別。  此基底類別是 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)。  雖然 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 介面被視為 C\+\+ 類別，但是 COM 並非專屬於任何一種語言，它可以在 C、PASCAL 或任何其他可支援 COM 物件之二進位配置的語言中實作。  
  
 OLE 會將所有衍生自 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 的類別視為「介面」。 這是一項重要的區別，因為 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 這類的「介面」並沒有實作。  它只會定義物件通訊所用的通訊協定，而不定義實作所執行的具體內容。  這對允許最大彈性的系統而言是合理的。  MFC 的工作是實作 MFC\/C\+\+ 程式的預設行為。  
  
 若要了解 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 的 MFC 實作，您必須先了解此介面。  簡化版本的 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 定義如下：  
  
```  
class IUnknown  
{  
public:  
    virtual HRESULT QueryInterface(REFIID iid, void** ppvObj) = 0;  
    virtual ULONG AddRef() = 0;  
    virtual ULONG Release() = 0;  
};  
```  
  
> [!NOTE]
>  某些必要的呼叫慣例詳細資料，例如此圖中省略了 `__stdcall`。  
  
 [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) 和 [Release](http://msdn.microsoft.com/library/windows/desktop/ms682317) 成員函式會控制物件的記憶體管理。  COM 使用參考計數配置來追蹤物件。  您永遠不會如同在 C\+\+ 中一般地參考物件。  相反地，一定會透過指標來參考 COM 物件。  若要在擁有者使用物件完成作業時釋放物件，會呼叫該物件的 [Release](http://msdn.microsoft.com/library/windows/desktop/ms682317) 成員 \(而不是使用運算子 delete，如同傳統的 C\+\+ 物件所為\)。  參考計數機制可讓單一物件的多個參考接受管理。  [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) 和 [Release](http://msdn.microsoft.com/library/windows/desktop/ms682317) 的實作會維護物件上的參考計數 \- 在參考計數達到零之前，都不會刪除物件。  
  
 從實作觀點來看，[AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) 和 [Release](http://msdn.microsoft.com/library/windows/desktop/ms682317) 都相當直接明瞭。  以下是一般實作：  
  
```  
ULONG CMyObj::AddRef()   
{   
    return ++m_dwRef;   
}  
  
ULONG CMyObj::Release()   
{   
    if (--m_dwRef == 0)   
    {  
        delete this;   
        return 0;  
    }  
    return m_dwRef;  
}  
```  
  
 [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) 成員函式更有趣。  擁有物件的成員函式僅有 [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) 和 [Release](http://msdn.microsoft.com/library/windows/desktop/ms682317) 並不吸引人 \- 如果可以告知物件執行比 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 所提供之內容還多的事情，一定會很棒。  這正是 [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) 的實用之處。  它可以讓您在相同的物件上取得不同的「介面」。  這些介面通常衍生自 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 並新增成員函式以新增其他功能。  COM 介面永遠不會有在介面中宣告的成員變數，且所有成員函式都宣告為純虛擬。  例如：  
  
```  
class IPrintInterface : public IUnknown  
{  
public:  
    virtual void PrintObject() = 0;  
};  
```  
  
 如果您只有一個 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)，若要取得 IPrintInterface，請使用 **IPrintInterface** 的 `IID` 呼叫 [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521)。  `IID` 是唯一可識別介面的 128 位元數字。  您或 OLE 定義的每個介面都有 `IID`。  如果 `pUnk` 是指向 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 物件的指標，從其擷取 IPrintInterface 的程式碼可能是：  
  
```  
IPrintInterface* pPrint = NULL;  
if (pUnk->QueryInterface(IID_IPrintInterface,   
    (void**)&pPrint) == NOERROR)  
{  
    pPrint->PrintObject();  
    pPrint->Release();     
        // release pointer obtained via QueryInterface  
}  
```  
  
 這好像相當簡單，但是您要如何實作支援 IPrintInterface 和 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 介面的物件？  在此情況下會很簡單，因為 IPrintInterface 直接衍生自 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) \- 藉由實作 IPrintInterface，即可自動支援 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)。  例如:  
  
```  
class CPrintObj : public CPrintInterface  
{  
    virtual HRESULT QueryInterface(REFIID iid, void** ppvObj);  
    virtual ULONG AddRef();  
    virtual ULONG Release();  
    virtual void PrintObject();  
};  
```  
  
 [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) 和 [Release](http://msdn.microsoft.com/library/windows/desktop/ms682317) 的實作就能和上述實作內容完全相同。  **CPrintObj::QueryInterface** 看起來應該類似這樣：  
  
```  
HRESULT CPrintObj::QueryInterface(REFIID iid, void FAR* FAR* ppvObj)  
{  
    if (iid == IID_IUnknown || iid == IID_IPrintInterface)  
    {  
        *ppvObj = this;  
        AddRef();  
        return NOERROR;  
    }  
    return E_NOINTERFACE;  
}  
```  
  
 如您所見，如果已辨識介面識別碼 \(IID\)，則會傳回指標給您的物件，否則就會發生錯誤。  另外請注意，成功的 [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) 會導致隱含的 [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379)。  當然，您也必須實作 CEditObj::Print。  這是很簡單的，因為 IPrintInterface 直接衍生自 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 介面。  不過，如果您想要支援兩個不同的介面，兩者都衍生自 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)，請考慮下列項目：  
  
```  
class IEditInterface : public IUnkown  
{  
public:  
    virtual void EditObject() = 0;  
};  
```  
  
 雖然有許多種不同的方式來實作支援 IEditInterface 和 IPrintInterface 的類別 \(包括使用 C\+\+ 多重繼承\)，但是此備註將著重於使用巢狀類別來實作這項功能。  
  
```  
class CEditPrintObj  
{  
public:  
    CEditPrintObj();  
  
    HRESULT QueryInterface(REFIID iid, void**);  
    ULONG AddRef();  
    ULONG Release();  
    DWORD m_dwRef;  
  
    class CPrintObj : public IPrintInterface  
    {  
    public:  
        CEditPrintObj* m_pParent;  
        virtual HRESULT QueryInterface(REFIID iid, void** ppvObj);  
        virtual ULONG AddRef();  
        virtual ULONG Release();  
    } m_printObj;  
  
    class CEditObj : public IEditInterface  
    {  
    public:  
        CEditPrintObj* m_pParent;  
        virtual ULONG QueryInterface(REFIID iid, void** ppvObj);  
        virtual ULONG AddRef();  
        virtual ULONG Release();  
    } m_editObj;  
};  
```  
  
 整個實作包含在下面：  
  
```  
CEditPrintObj::CEditPrintObj()  
{  
    m_editObj.m_pParent = this;  
    m_printObj.m_pParent = this;  
}  
  
ULONG CEditPrintObj::AddRef()   
{   
    return ++m_dwRef;  
}  
  
CEditPrintObj::Release()  
{  
    if (--m_dwRef == 0)  
    {  
        delete this;  
        return 0;  
    }  
    return m_dwRef;  
}  
  
HRESULT CEditPrintObj::QueryInterface(REFIID iid, void** ppvObj)  
{  
    if (iid == IID_IUnknown || iid == IID_IPrintInterface)  
    {  
        *ppvObj = &m_printObj;  
        AddRef();  
        return NOERROR;  
    }  
    else if (iid == IID_IEditInterface)  
    {  
        *ppvObj = &m_editObj;  
        AddRef();  
        return NOERROR;  
    }  
    return E_NOINTERFACE;  
}  
  
ULONG CEditPrintObj::CEditObj::AddRef()   
{   
    return m_pParent->AddRef();   
}  
  
ULONG CEditPrintObj::CEditObj::Release()   
{   
    return m_pParent->Release();   
}  
  
HRESULT CEditPrintObj::CEditObj::QueryInterface(  
    REFIID iid, void** ppvObj)   
{   
    return m_pParent->QueryInterface(iid, ppvObj);   
}  
  
ULONG CEditPrintObj::CPrintObj::AddRef()   
{   
    return m_pParent->AddRef();   
}  
  
ULONG CEditPrintObj::CPrintObj::Release()   
{   
    return m_pParent->Release();   
}  
  
HRESULT CEditPrintObj::CPrintObj::QueryInterface(  
    REFIID iid, void** ppvObj)   
{   
    return m_pParent->QueryInterface(iid, ppvObj);   
}  
```  
  
 請注意，大部分的 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 實作都會放入 CEditPrintObj 類別而不是複製 CEditPrintObj::CEditObj 和 CEditPrintObj::CPrintObj 中的程式碼。  這樣可以減少程式碼數量，並且避免錯誤。  此處的重點是可從 IUnknown 介面呼叫 [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) 以擷取物件可能支援的任何介面，而且可從每個介面執行相同動作。  這表示從每個介面皆可用的所有 [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) 必須有完全相同的行為方式。  為了讓這些內嵌物件呼叫「外部物件」中的實作，需使用返回指標 \(m\_pParent\)。  M\_pParent 指標會在 CEditPrintObj 建構函式期間初始化。  然後您也會實作 CEditPrintObj::CPrintObj::PrintObject 和 CEditPrintObj::CEditObj::EditObject。  新增許多程式碼以新增一項功能 \- 編輯物件的功能。  幸運的是，介面很少只具有單一個成員函式 \(雖然還是會發生\)，在此情況下，EditObject 和 PrintObject 通常會結合成單一介面。  
  
 這是此簡單案例的許多種解釋及許多程式碼。  MFC\/OLE 類別提供更簡單的替代方案。  MFC 實作所使用的技術和利用訊息對應包裝 Windows 訊息的方法類似。  這項功能稱為*介面對應*，將於下一節討論。  
  
## MFC 介面對應  
 MFC\/OLE 所包含的「介面對應」實作在概念和執行上與 MFC 的「訊息對應」和「分派對應」相似。  MFC 介面對應的核心功能如下所示：  
  
-   [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 的標準實作，內建於 `CCmdTarget` 類別中。  
  
-   參考計數的維護，由 [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) 和 [Release](http://msdn.microsoft.com/library/windows/desktop/ms682317) 修改  
  
-   [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) 的資料驅動實作  
  
 此外，介面對應支援下列進階功能：  
  
-   支援建立可彙總的 COM 物件  
  
-   支援使用 COM 物件實作中的彙總物件  
  
-   實作且可攔截且可延伸  
  
 如需彙總的詳細資訊，請參閱[彙總](http://msdn.microsoft.com/library/windows/desktop/ms686558\(v=vs.85\).aspx)主題。  
  
 MFC 的介面對應支援以 `CCmdTarget` 類別為基礎。  `CCmdTarget` "*has\-a*" 參考計數以及所有和 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 實作相關聯的成員函式 \(例如，參考計數位於 `CCmdTarget`\)。  若要建立支援 OLE COM 的類別，您要從 `CCmdTarget` 衍生類別，並使用不同的巨集和 `CCmdTarget` 的成員函式實作所需的介面。  MFC 的實作使用巢狀類別定義如同上述範例中的每個介面實作。  利用 IUnknown 的標準實作以及許多會排除部分重複程式碼的巨集，可以更方便進行。  
  
## 介面對應基本知識  
  
#### 使用 MFC 的介面對應實作一個類別  
  
1.  直接或間接從 `CCmdTarget` 衍生類別。  
  
2.  使用衍生類別定義中的 `DECLARE_INTERFACE_MAP` 函式。  
  
3.  針對您想要支援的每個介面，使用類別定義中的 `BEGIN_INTERFACE_PART` 和 `END_INTERFACE_PART` 巨集。  
  
4.  在實作檔案中，使用 `BEGIN_INTERFACE_MAP` 和 `END_INTERFACE_MAP` 巨集來定義類別的介面對應。  
  
5.  針對受支援的每個 IID，使用 `BEGIN_INTERFACE_MAP` 和 `END_INTERFACE_MAP` 巨集之間的 `INTERFACE_PART` 巨集，將該 IID 對應至類別的特定「部分」。  
  
6.  實作代表您支援之介面的每個巢狀類別。  
  
7.  使用 `METHOD_PROLOGUE` 巨集來存取父代的 `CCmdTarget` 衍生物件。  
  
8.  [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379)、[Release](http://msdn.microsoft.com/library/windows/desktop/ms682317) 和 [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) 可以委派給這些函式的 `CCmdTarget` 實作 \(`ExternalAddRef`、`ExternalRelease` 和 `ExternalQueryInterface`\)。  
  
 上述的 CPrintEditObj 範例可以下列方式實作：  
  
```  
class CPrintEditObj : public CCmdTarget  
{  
public:  
    // member data and member functions for CPrintEditObj go here  
  
// Interface Maps  
protected:  
    DECLARE_INTERFACE_MAP()  
  
    BEGIN_INTERFACE_PART(EditObj, IEditInterface)  
        STDMETHOD_(void, EditObject)();  
    END_INTERFACE_PART(EditObj)  
  
    BEGIN_INTERFACE_PART(PrintObj, IPrintInterface)  
        STDMETHOD_(void, PrintObject)();  
    END_INTERFACE_PART(PrintObj)  
};  
```  
  
 上述宣告會建立一個衍生自 `CCmdTarget` 的類別。  `DECLARE_INTERFACE_MAP` 巨集會告知架構這個類別會有自訂介面對應。  此外，`BEGIN_INTERFACE_PART` 和 `END_INTERFACE_PART` 巨集會定義巢狀類別，在此情況下會使用 CEditObj 和 CPrintObj 等名稱 \(X 只能用來區分巢狀類別和 "C" 開頭的全域類別以及 "I" 開頭的介面類別\)。  這些類別的兩個巢狀成員隨即建立：分別是 m\_CEditObj 和 m\_CPrintObj。  巨集會自動宣告 [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379)、[Release](http://msdn.microsoft.com/library/windows/desktop/ms682317) 和 [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) 函式，因此您只會宣告此介面的特定函式：EditObject 和 PrintObject \(使用 OLE 巨集 `STDMETHOD`，以提供適用於目標平台的 `_stdcall` 和虛擬關鍵字\)。  
  
 實作這個類別的介面對應：  
  
```  
BEGIN_INTERFACE_MAP(CPrintEditObj, CCmdTarget)  
    INTERFACE_PART(CPrintEditObj, IID_IPrintInterface, PrintObj)  
    INTERFACE_PART(CPrintEditObj, IID_IEditInterface, EditObj)  
END_INTERFACE_MAP()  
```  
  
 這能分別讓 IID\_IPrintInterface IID 和 m\_CPrintObj 連結，讓 IID\_IEditInterface 和 m\_CEditObj 連結。  [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) \(`CCmdTarget::ExternalQueryInterface`\) 的 `CCmdTarget` 實作會使用此對應在收到要求時將指標傳回 m\_CPrintObj 和 m\_CEditObj。  不需要包含 `IID_IUnknown` 的項目；架構將在要求 `IID_IUnknown` 時使用對應中的第一個介面 \(在此情況下為 m\_CPrintObj\)。  
  
 即使 `BEGIN_INTERFACE_PART` 巨集自動為您宣告 [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379)、[Release](http://msdn.microsoft.com/library/windows/desktop/ms682317) 和 [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) 函式，您仍然需要實作它們：  
  
```  
ULONG FAR EXPORT CEditPrintObj::XEditObj::AddRef()  
{  
    METHOD_PROLOGUE(CEditPrintObj, EditObj)  
    return pThis->ExternalAddRef();  
}  
  
ULONG FAR EXPORT CEditPrintObj::XEditObj::Release()  
{  
    METHOD_PROLOGUE(CEditPrintObj, EditObj)  
    return pThis->ExternalRelease();  
}  
  
HRESULT FAR EXPORT CEditPrintObj::XEditObj::QueryInterface(  
    REFIID iid, void FAR* FAR* ppvObj)  
{  
    METHOD_PROLOGUE(CEditPrintObj, EditObj)  
    return (HRESULT)pThis->ExternalQueryInterface(&iid, ppvObj);  
}  
  
void FAR EXPORT CEditPrintObj::XEditObj::EditObject()  
{  
    METHOD_PROLOGUE(CEditPrintObj, EditObj)  
    // code to "Edit" the object, whatever that means...  
}  
```  
  
 CEditPrintObj::CPrintObj 的實作會類似上述 CEditPrintObj::CEditObj 的定義。  雖然有可能建立用來自動產生這些函式的巨集 \(但是在稍早的 MFC\/OLE 開發中就是這樣的情況\)，但是很難在巨集產生一行以上的程式碼時設定中斷點。  基於這個理由，這個程式碼會以手動方式展開。  
  
 藉由使用訊息對應的架構實作，有一些不一定需要執行的動作：  
  
-   實作 QueryInterface  
  
-   實作 AddRef 和 Release  
  
-   在兩個介面上宣告其中一種內建方法  
  
 此外，架構會在內部使用訊息對應。  這可讓您從架構類別衍生，例如 `COleServerDoc`，已經支援特定介面並提供架構所提供之介面的取代或新增項目。  您可以執行這個動作，因為架構完全支援從基底類別繼承介面對應。  這就是為何 `BEGIN_INTERFACE_MAP` 接受基底類別的名稱做為其第二個參數的原因。  
  
> [!NOTE]
>  它通常無法僅藉由從 MFC 版本繼承介面的內嵌特製化，就能重複使用 OLE 介面之 MFC 內建實作的實作。  這是不可能的，因為使用 `METHOD_PROLOGUE` 巨集存取包含性且衍生自 `CCmdTarget` 的物件表示衍生自 `CCmdTarget` 的物件之內嵌物件的*固定位移*。  例如，這就表示您無法從 `COleClientItem::XAdviseSink` 中的 MFC 實作衍生內嵌的 XMyAdviseSink，因為 XAdviseSink 依賴位於來自 `COleClientItem` 物件頂端的特定位移。  
  
> [!NOTE]
>  不過，您可以將所有您希望其成為 MFC 預設行為的函式委派給 MFC 實作。  這是 `COleFrameHook` 類別中 `IOleInPlaceFrame` \(XOleInPlaceFrame\) 的 MFC 實作 \(它會將許多函數委派至 m\_xOleInPlaceUIWindow\)。  選擇此設計可減少實作許多介面之物件的執行階段大小，排除對返回指標的需求 \(如前一節中使用的方式 m\_pParent\)。  
  
### 彙總與介面對應  
 除了支援獨立的 COM 物件，MFC 也支援彙總。  要在此討論彙總是個太複雜的主題。請參閱[彙總](http://msdn.microsoft.com/library/windows/desktop/ms686558\(v=vs.85\).aspx)主題以取得彙總的詳細資訊。  這個註解只描述對內建於架構和介面對應中的彙總支援。  
  
 有兩種方式來使用彙總：\(1\) 使用支援彙總的 COM 物件，以及 \(2\) 實作可由另一個物件彙總的物件。  這些功能可以稱為「使用彙總物件」和「使物件彙總」。  MFC 兩者皆可支援。  
  
### 使用彙總物件  
 若要使用彙總物件，則必須有某種方式將彙總繫結到 QueryInterface 機制。  換句話說，彙總物件的行為必須如同物件的原生組件一般。  如何繫結到 MFC 的介面對應機制？  除了 `INTERFACE_PART` 巨集 \(其中的巢狀物件對應至 IID\)，您也可以宣告彙總物件為衍生自 `CCmdTarget` 之類別的一部分。  若要這樣做，需使用 `INTERFACE_AGGREGATE` 巨集。  這可讓您指定成員變數 \(必須是指向 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 或衍生類別的指標\)，將其整合到介面對應機制中。  如果指標不是 NULL，在呼叫 `CCmdTarget::ExternalQueryInterface` 時，如果要求的 `IID` 不屬於 `CCmdTarget` 物件本身所支援的其中一個原生 `IID`，此架構會自動呼叫彙總物件的 [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) 成員函式。  
  
##### 使用 INTERFACE\_AGGREGATE 巨集  
  
1.  宣告成員變數 \(`IUnknown*`\)，此變數包含指向彙總物件的指標。  
  
2.  在介面對應中包含 `INTERFACE_AGGREGATE` 巨集，它會依名稱參考成員變數。  
  
3.  在某個時間點 \(通常是在 `CCmdTarget::OnCreateAggregates` 期間\)，將成員變數初始化為 NULL 以外的成員變數。  
  
 例如:  
  
```  
class CAggrExample : public CCmdTarget  
{  
public:  
    CAggrExample();  
  
protected:  
    LPUNKNOWN m_lpAggrInner;  
    virtual BOOL OnCreateAggregates();  
  
    DECLARE_INTERFACE_MAP()  
    // "native" interface part macros may be used here  
};  
  
CAggrExample::CAggrExample()  
{  
    m_lpAggrInner = NULL;  
}  
  
BOOL CAggrExample::OnCreateAggregates()  
{  
    // wire up aggregate with correct controlling unknown  
    m_lpAggrInner = CoCreateInstance(CLSID_Example,  
        GetControllingUnknown(), CLSCTX_INPROC_SERVER,  
        IID_IUnknown, (LPVOID*)&m_lpAggrInner);  
    if (m_lpAggrInner == NULL)  
        return FALSE;  
    // optionally, create other aggregate objects here  
    return TRUE;  
}  
  
BEGIN_INTERFACE_MAP(CAggrExample, CCmdTarget)  
    // native "INTERFACE_PART" entries go here  
    INTERFACE_AGGREGATE(CAggrExample, m_lpAggrInner)  
END_INTERFACE_MAP()  
```  
  
 m\_lpAggrInner 變數會在建構函式中初始化為 NULL。  此架構會忽略預設 [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) 實作中的 NULL 成員變數。  `OnCreateAggregates` 是實際建立彙總物件的好地方。  如果您正在建立 `COleObjectFactory` MFC 實作外部的物件，您必須明確地呼叫它。  討論到建立彙總物件時，在 `CCmdTarget::OnCreateAggregates` 中建立彙總和使用 `CCmdTarget::GetControllingUnknown` 的原因將會變得很明確。  
  
 這項技術可提供您的物件彙總物件支援的所有介面及其原生介面。  如果您只想要彙總支援介面的子集，您可以覆寫 `CCmdTarget::GetInterfaceHook`。  這可讓您取得非常低層級的攔截性，類似 [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521)。  您通常會想要彙總支援的所有介面。  
  
### 讓物件實作可以彙總  
 若要讓物件可以彙總，[AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379)、[Release](http://msdn.microsoft.com/library/windows/desktop/ms682317) 和 [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) 必須委派給 "controlling unknown"。 換句話說，若要讓它成為物件的一部分，它必須委派 [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379)、[Release](http://msdn.microsoft.com/library/windows/desktop/ms682317) 和 [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) 給不同的物件，也要衍生自 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)。  這個 "controlling unknown" 可在建立物建時提供給物件，亦即提供給 `COleObjectFactory` 的實作。  實作此項目會帶來少量的額外負荷，在某些情況下不需要這樣做，因此 MFC 使其為選擇性項目。  若要讓物件彙總，您可以從物件的建構函式呼叫 `CCmdTarget::EnableAggregation`。  
  
 如果物件也使用彙總，您也必須確定傳遞正確的 "controlling unknown" 給彙總物件。  通常此 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 指標會在建立彙總時傳遞給物件。  例如，pUnkOuter 參數是利用 `CoCreateInstance` 建立之物建的 "controlling unknown"。  正確的 "controlling unknown" 指標可以藉由呼叫 `CCmdTarget::GetControllingUnknown` 擷取。  然而，從函式傳回的值在建構函式期間無效。  基於這個理由，即使是從 `COleObjectFactory` 實作建立彙總，建議您只在 `CCmdTarget::OnCreateAggregates` 的覆寫中建立彙總，其中從 `GetControllingUnknown` 的傳回值是可靠的。  
  
 另一個重點是物件在新增或釋放假造的參考計數時會管理正確的參考計數。  若要確保此情況，請務必呼叫 `ExternalAddRef` 和 `ExternalRelease` 而不是 `InternalRelease` 和 `InternalAddRef`。  我們很少在支援彙總的類別上呼叫 `InternalRelease` 或 `InternalAddRef`。  
  
### 參考資料  
 OLE 的進階用法，例如定義您自己的介面或覆寫架構的 OLE 介面實作，需要使用基礎的介面對應機制。  
  
 本節討論可用來實作這些進階功能的每個巨集和 API。  
  
### CCmdTarget::EnableAggregation — 函式描述  
  
```  
  
void EnableAggregation();  
```  
  
## 備註  
 如果您想要支援此類型物件的 OLE 彙總，請在衍生類別的建構函式中呼叫此函式。  這會準備可彙總物建所需的特殊 IUnknown 實作。  
  
### CCmdTarget::ExternalQueryInterface \- 函式描述  
  
```  
  
              DWORD ExternalQueryInterface(    const void FAR* lpIID,    LPVOID FAR* ppvObj   
);  
```  
  
## 備註  
  
#### 參數  
 `lpIID`  
 指向 IID 的遠端指標 \(QueryInterface 的第一個引數\)  
  
 `ppvObj`  
 指向 IUnknown\* 的指標 \(QueryInterface 的第二個引數\)  
  
## 備註  
 在 IUnknown 實作中為類別實作的每個介面呼叫此函式。  此函式會根據物件的介面對應，提供 QueryInterface 的標準資料導向實作。  它是將傳回值轉換為 HRESULT 的必要項。  如果已彙總物件，此函式會呼叫 "controlling IUnknown"，而不是使用本機介面對應。  
  
### CCmdTarget::ExternalAddRef \- 函式描述  
  
```  
  
DWORD ExternalAddRef();  
```  
  
## 備註  
 在 IUnknown::AddRef 實作中為類別實作的每個介面呼叫此函式。  傳回值是 CCmdTarget 物件上的新參考計數。  如果已彙總物件，此函式會呼叫 "controlling IUnknown"，而不是管理本機參考計數。  
  
### CCmdTarget::ExternalRelease \- 函式描述  
  
```  
  
DWORD ExternalRelease();  
  
```  
  
## 備註  
 在 IUnknown::Release 實作中為類別實作的每個介面呼叫此函式。  傳回的值表示物件上的新參考計數。  如果已彙總物件，此函式會呼叫 "controlling IUnknown"，而不是管理本機參考計數。  
  
### DECLARE\_INTERFACE\_MAP \- 巨集描述  
  
```  
  
DECLARE_INTERFACE_MAP  
  
```  
  
## 備註  
 在衍生自具有介面對應之 `CCmdTarget` 的任何類別中使用這個巨集。  其用法與 `DECLARE_MESSAGE_MAP` 非常類似。  這個巨集引動過程應該放在類別定義中，通常是在標頭 \(.H\) 檔案中。  具有 `DECLARE_INTERFACE_MAP` 的類別必須利用 `BEGIN_INTERFACE_MAP` 和 `END_INTERFACE_MAP` 巨集在實作檔案 \(.CPP\) 中定義介面對應。  
  
### BEGIN\_INTERFACE\_PART 和 END\_INTERFACE\_PART \- 巨集描述  
  
```  
  
              BEGIN_INTERFACE_PART(   
   localClass,  
   iface   
);  
END_INTERFACE_PART(   
   localClass   
)  
```  
  
## 備註  
  
#### 參數  
 l`ocalClass`  
 實作介面的類別名稱。  
  
 `iface`  
 這個類別實作的介面名稱。  
  
## 備註  
 針對類別將實作的每個介面，您必須具有 `BEGIN_INTERFACE_PART` 和 `END_INTERFACE_PART` 配對。  這些巨集會定義衍生自您定義之 OLE 介面的本機類別，並且定義該類別的內嵌成員變數。  [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379)、[Release](http://msdn.microsoft.com/library/windows/desktop/ms682317) 和 [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) 成員會自動宣告。  您必須包含對屬於所實作之介面的其他成員函式的宣告 \(這些宣告位於 `BEGIN_INTERFACE_PART` 和 `END_INTERFACE_PART` 巨集之間\)。  
  
 `iface` 引數是您想要實作的 OLE 介面，例如 `IAdviseSink` 或 `IPersistStorage` \(或您自己的自訂介面\)。  
  
 `localClass` 引數是將要定義之本機類別的名稱。  ' X' 將會自動加在名稱前面。  此命名慣例用來避免和相同名稱之全域類別的衝突。  此外，除了 'm\_x' 前置詞以外，內嵌成員的名稱和 `localClass` 的名稱相同。  
  
 例如:  
  
```  
BEGIN_INTERFACE_PART(MyAdviseSink, IAdviseSink)  
   STDMETHOD_(void,OnDataChange)(LPFORMATETC, LPSTGMEDIUM);  
   STDMETHOD_(void,OnViewChange)(DWORD, LONG);  
   STDMETHOD_(void,OnRename)(LPMONIKER);  
   STDMETHOD_(void,OnSave)();  
   STDMETHOD_(void,OnClose)();  
END_INTERFACE_PART(MyAdviseSink)  
```  
  
 會定義衍生自 IAdviseSink 且名為 XMyAdviseSink 的本機類別，並定義該類別在其中宣告為 m\_xMyAdviseSink.Note 的類別成員：  
  
> [!NOTE]
>  基本上，以 `STDMETHOD`\_ 開頭的行會從 OLE2.H 複製並稍加修改。  從 OLE2.H 將其複製可以減少很難解決的錯誤。  
  
### BEGIN\_INTERFACE\_MAP 和 END\_INTERFACE\_MAP \- 巨集描述  
  
```  
  
              BEGIN_INTERFACE_MAP(   
   theClass,  
   baseClass   
) END_INTERFACE_MAP  
```  
  
## 備註  
  
#### 參數  
 `theClass`  
 在其中定義介面對應的類別  
  
 `baseClass`  
 從中衍生 `theClass` 的類別。  
  
## 備註  
 `BEGIN_INTERFACE_MAP` 和 `END_INTERFACE_MAP` 巨集在實作檔案中用來實際定義介面對應。  每個實作的介面都有一個以上的 `INTERFACE_PART` 巨集引動過程。  類別使用的每個彙總都有一個 `INTERFACE_AGGREGATE` 巨集引動過程。  
  
### INTERFACE\_PART \- 巨集描述  
  
```  
  
              INTERFACE_PART(   
   theClass,  
   iid,   
   localClass   
)  
```  
  
## 備註  
  
#### 參數  
 `theClass`  
 包含介面對應的類別名稱。  
  
 `iid`  
 要對應到內嵌類別的 `IID`。  
  
 `localClass`  
 本機類別的名稱 \(減去 'X'\)。  
  
## 備註  
 對於物件將支援的每個介面而言，這個巨集可在 `BEGIN_INTERFACE_MAP` 巨集和 `END_INTERFACE_MAP` 巨集之間使用。  它可讓您將 IID 對應至 `theClass` 和 `localClass` 所指定的成員。  'm\_x' 將會自動新增至 `localClass`。  請注意，一個以上的 `IID` 會與單一成員相關聯。  當您只實作「最常衍生的」介面，並且想要提供所有中繼介面時，這會非常實用。  一個良好的範例是 `IOleInPlaceFrameWindow` 介面。  它的階層看起來像這樣：  
  
```  
IUnknown  
    IOleWindow  
        IOleUIWindow  
            IOleInPlaceFrameWindow  
```  
  
 如果物件實作 `IOleInPlaceFrameWindow`，除了「最常衍生的」介面 `IOleInPlaceFrameWindow` \(即您實際實作的介面\)，用戶端可能會在任何介面上 `QueryInterface`：`IOleUIWindow`、`IOleWindow` 或 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)。  若要處理這個問題，您可以使用一個以上的 `INTERFACE_PART` 巨集將每個基底介面對應至 `IOleInPlaceFrameWindow` 介面：  
  
 在類別定義檔中：  
  
```  
BEGIN_INTERFACE_PART(CMyFrameWindow, IOleInPlaceFrameWindow)  
```  
  
 在類別實作檔中：  
  
```  
BEGIN_INTERFACE_MAP(CMyWnd, CFrameWnd)  
    INTERFACE_PART(CMyWnd, IID_IOleWindow, MyFrameWindow)  
    INTERFACE_PART(CMyWnd, IID_IOleUIWindow, MyFrameWindow)  
    INTERFACE_PART(CMyWnd, IID_IOleInPlaceFrameWindow, MyFrameWindow)  
END_INTERFACE_MAP  
```  
  
 架構會負責 IUnknown，因為它一律為必要項。  
  
### INTERFACE\_PART \- 巨集描述  
  
```  
  
              INTERFACE_AGGREGATE(   
   theClass,  
   theAggr   
)  
```  
  
## 備註  
  
#### 參數  
 `theClass`  
 包含介面對應的類別名稱，  
  
 `theAggr`  
 要彙總的成員變數名稱。  
  
## 備註  
 這個巨集可用來告知架構類別正在使用彙總物件。  它必須出現在 `BEGIN_INTERFACE_PART` 和 `END_INTERFACE_PART` 巨集之間。  彙總物件是個別的物件，並衍生自 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)。  藉由使用彙總和 `INTERFACE_AGGREGATE` 巨集，您可以讓彙總支援的所有介面直接受物件支援。  `theAggr` 引數是衍生自 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) \(直接或間接\) 之類別的成員變數名稱。  所有 `INTERFACE_AGGREGATE` 巨集在位於介面對應中時必須遵循 `INTERFACE_PART` 巨集。  
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)
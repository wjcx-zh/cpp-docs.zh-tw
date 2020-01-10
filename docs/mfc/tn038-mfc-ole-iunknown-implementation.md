---
title: TN038： MFC-OLE IUnknown 執行
ms.date: 06/28/2018
helpviewer_keywords:
- aggregation macros [MFC]
- COM interfaces, base interface
- IUnknown interface
- END_INTERFACE_MAP macro [MFC]
- TN038
- BEGIN_INTERFACE_PART macro [MFC]
- DECLARE_INTERFACE_MAP macro [MFC]
- BEGIN_INTERFACE_MAP macro [MFC]
- OLE [MFC], implementing IUnknown interface
- METHOD_PROLOGUE macro [MFC]
- STDMETHOD macro [MFC]
- END_INTERFACE_PART macro [MFC]
- INTERFACE_PART macro
ms.assetid: 19d946ba-beaf-4881-85c6-0b598d7f6f11
ms.openlocfilehash: 9ceb903ec38bc0ad7cfdee1c59babd2379422ac3
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302350"
---
# <a name="tn038-mfcole-iunknown-implementation"></a>TN038：MFC/OLE IUnknown 實作

> [!NOTE]
> 下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

OLE 2 的核心是「OLE 元件物件模型」或 COM。 COM 會定義合作物件如何彼此通訊的標準。 這包括「物件」外觀的詳細資料，包括如何在物件上分派方法。 COM 也會定義所有 COM 相容類別從其中衍生的基底類別。 這個基類是[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)。 雖然[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)介面稱為C++類別，但 COM 並非專屬於任何一種語言，它可以在 C、PASCAL 或任何其他可支援 COM 物件之二進位配置的語言中執行。

OLE 是指衍生自[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)做為「介面」的所有類別。 這是一項重要的差異，因為[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)之類的「介面」不會執行任何程式。 它只會定義物件通訊所用的通訊協定，而不定義實作所執行的具體內容。 這對允許最大彈性的系統而言是合理的。 MFC 的工作是實作 MFC/C++ 程式的預設行為。

若要瞭解 MFC 的[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)執行，您必須先瞭解此介面的意義。 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)的簡化版本定義如下：

```cpp
class IUnknown
{
public:
    virtual HRESULT QueryInterface(REFIID iid, void** ppvObj) = 0;
    virtual ULONG AddRef() = 0;
    virtual ULONG Release() = 0;
};
```

> [!NOTE]
> 某些必要的呼叫慣例詳細資料，例如此圖中省略了 `__stdcall`。

[AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)和[Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)成員函式會控制物件的記憶體管理。 COM 使用參考計數配置來追蹤物件。 您永遠不會如同在 C++ 中一般地參考物件。 相反地，一定會透過指標來參考 COM 物件。 若要在擁有者使用它完成時釋放物件，會呼叫物件的[release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)成員（而不是使用運算子 delete，如同傳統C++物件所做的一樣）。 參考計數機制可讓單一物件的多個參考接受管理。 [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)和[Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)的執行會維護物件上的參考計數，除非物件的參考計數達到零，否則不會刪除它。

從執行的觀點來看， [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)和[發行](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)相當簡單。 以下是一般實作：

```cpp
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

[QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))成員函式有點有趣。 只有成員函式是[AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)和[Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)的物件並不是很有趣的，告訴物件執行的動作比[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)提供的還要多。 這就是[QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))很有用的地方。 它可以讓您在相同的物件上取得不同的「介面」。 這些介面通常衍生自[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) ，並藉由加入新的成員函式來新增額外的功能。 COM 介面永遠不會有在介面中宣告的成員變數，且所有成員函式都宣告為純虛擬。 例如，套用至物件的

```cpp
class IPrintInterface : public IUnknown
{
public:
    virtual void PrintObject() = 0;
};
```

如果您只有一個[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)，若要取得 IPrintInterface，請使用 `IPrintInterface`的 `IID` 呼叫[QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) 。 `IID` 是唯一可識別介面的 128 位元數字。 您或 OLE 定義的每個介面都有 `IID`。 如果*pUnk*是[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)物件的指標，從中取得 IPrintInterface 的程式碼可能是：

```cpp
IPrintInterface* pPrint = NULL;
if (pUnk->QueryInterface(IID_IPrintInterface, (void**)&pPrint) == NOERROR)
{
    pPrint->PrintObject();
    pPrint->Release();
    // release pointer obtained via QueryInterface
}
```

這似乎相當簡單，但您要如何在此情況下，同時支援 IPrintInterface 和[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)介面的物件，因為 IPrintInterface 是直接衍生自[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) （藉由執行 IPrintInterface），所以會自動支援[iunknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 。 例如：

```cpp
class CPrintObj : public CPrintInterface
{
    virtual HRESULT QueryInterface(REFIID iid, void** ppvObj);
    virtual ULONG AddRef();
    virtual ULONG Release();
    virtual void PrintObject();
};
```

[AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)和[Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)的執行方式與上述所實的一樣。 `CPrintObj::QueryInterface` 看起來會像這樣：

```cpp
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

如您所見，如果已辨識介面識別碼 (IID)，則會傳回指標給您的物件，否則就會發生錯誤。 另請注意，成功的[QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))會導致隱含的[AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)。 當然，您也必須實作 CEditObj::Print。 這很簡單，因為 IPrintInterface 直接衍生自[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)介面。 不過，如果您想要支援兩個不同的介面，兩者都衍生自[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)，請考慮下列各項：

```cpp
class IEditInterface : public IUnkown
{
public:
    virtual void EditObject() = 0;
};
```

雖然有許多種不同的方式來實作支援 IEditInterface 和 IPrintInterface 的類別 (包括使用 C++ 多重繼承)，但是此備註將著重於使用巢狀類別來實作這項功能。

```cpp
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

```cpp
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

HRESULT CEditPrintObj::CEditObj::QueryInterface(REFIID iid, void** ppvObj)
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

HRESULT CEditPrintObj::CPrintObj::QueryInterface(REFIID iid, void** ppvObj)
{
    return m_pParent->QueryInterface(iid, ppvObj);
}
```

請注意，大部分的[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)執行都會放入 CEditPrintObj 類別中，而不是複製 CEditPrintObj：： CEditObj 和 CEditPrintObj：： CPrintObj 中的程式碼。 這樣可以減少程式碼數量，並且避免錯誤。 此處的重點是，從 IUnknown 介面可以呼叫[QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))來抓取物件可能支援的任何介面，而且可以從每個介面執行相同的動作。 這表示每個介面中可用的所有[QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))函數都必須完全相同的行為。 為了讓這些內嵌物件呼叫「外部物件」中的實作，需使用返回指標 (m_pParent)。 M_pParent 指標會在 CEditPrintObj 建構函式期間初始化。 然後您也會實作 CEditPrintObj::CPrintObj::PrintObject 和 CEditPrintObj::CEditObj::EditObject。 新增許多程式碼以新增一項功能 - 編輯物件的功能。 幸運的是，介面很少只具有單一個成員函式 (雖然還是會發生)，在此情況下，EditObject 和 PrintObject 通常會結合成單一介面。

這是此簡單案例的許多種解釋及許多程式碼。 MFC/OLE 類別提供更簡單的替代方案。 MFC 實作所使用的技術和利用訊息對應包裝 Windows 訊息的方法類似。 這項功能稱為*介面對應*，將在下一節中討論。

## <a name="mfc-interface-maps"></a>MFC 介面對應

MFC/OLE 所包含的「介面對應」實作在概念和執行上與 MFC 的「訊息對應」和「分派對應」相似。 MFC 介面對應的核心功能如下所示：

- [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)的標準執行，內建于 `CCmdTarget` 類別中。

- 參考計數的維護，由[AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)和[發行](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)修改

- [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))的資料驅動型執行

此外，介面對應支援下列進階功能：

- 支援建立可彙總的 COM 物件

- 支援使用 COM 物件實作中的彙總物件

- 實作且可攔截且可延伸

如需匯總的詳細資訊，請參閱[匯總](/windows/win32/com/aggregation)主題。

MFC 的介面對應支援以 `CCmdTarget` 類別為基礎。 `CCmdTarget` 「*具有-a*」參考計數，以及與[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)執行相關聯的所有成員函式（例如，參考計數在 `CCmdTarget`中）。 若要建立支援 OLE COM 的類別，您要從 `CCmdTarget` 衍生類別，並使用不同的巨集和 `CCmdTarget` 的成員函式實作所需的介面。 MFC 的實作使用巢狀類別定義如同上述範例中的每個介面實作。 利用 IUnknown 的標準實作以及許多會排除部分重複程式碼的巨集，可以更方便進行。

## <a name="interface-map-basics"></a>介面對應基本知識

### <a name="to-implement-a-class-using-mfcs-interface-maps"></a>使用 MFC 的介面對應實作一個類別

1. 直接或間接從 `CCmdTarget` 衍生類別。

2. 使用衍生類別定義中的 `DECLARE_INTERFACE_MAP` 函式。

3. 針對您想要支援的每個介面，使用 BEGIN_INTERFACE_PART，並 END_INTERFACE_PART 類別定義中的宏。

4. 在執行檔中，使用 BEGIN_INTERFACE_MAP 並 END_INTERFACE_MAP 宏來定義類別的介面對應。

5. 針對每個支援的 IID，請使用 BEGIN_INTERFACE_MAP 和 END_INTERFACE_MAP 宏之間的 INTERFACE_PART 宏，將該 IID 對應至類別的特定「部分」。

6. 實作代表您支援之介面的每個巢狀類別。

7. 使用 METHOD_PROLOGUE 宏來存取父系、`CCmdTarget`衍生的物件。

8. [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)、 [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)和[QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))可以委派給這些函式的 `CCmdTarget` 實作為（`ExternalAddRef`、`ExternalRelease`和 `ExternalQueryInterface`）。

上述的 CPrintEditObj 範例可以下列方式實作：

```cpp
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

上述宣告會建立一個衍生自 `CCmdTarget` 的類別。 DECLARE_INTERFACE_MAP 宏會告訴架構，此類別將會有自訂的介面對應。 此外，BEGIN_INTERFACE_PART 和 END_INTERFACE_PART 宏會定義嵌套類別，在此案例中，名稱為 CEditObj 和 CPrintObj （X 只能用來區別開頭為 "C" 的全域類別和介面類別別，開頭為 "I"）。 這些類別的兩個巢狀成員隨即建立：分別是 m_CEditObj 和 m_CPrintObj。 宏會自動宣告[AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)、 [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)和[QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))函式;因此，您只會宣告此介面特有的函式： EditObject 和 PrintObject （使用 OLE 宏 STDMETHOD，以便為目標平臺提供適當的 **_stdcall**和虛擬關鍵字）。

實作這個類別的介面對應：

```cpp
BEGIN_INTERFACE_MAP(CPrintEditObj, CCmdTarget)
    INTERFACE_PART(CPrintEditObj, IID_IPrintInterface, PrintObj)
    INTERFACE_PART(CPrintEditObj, IID_IEditInterface, EditObj)
END_INTERFACE_MAP()
```

這能分別讓 IID_IPrintInterface IID 和 m_CPrintObj 連結，讓 IID_IEditInterface 和 m_CEditObj 連結。 [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) （`CCmdTarget::ExternalQueryInterface`）的 `CCmdTarget` 執行會使用此對應，在要求時傳回 m_CPrintObj 和 m_CEditObj 的指標。 不需要包含 `IID_IUnknown` 的項目；架構將在要求 `IID_IUnknown` 時使用對應中的第一個介面 (在此情況下為 m_CPrintObj)。

雖然 BEGIN_INTERFACE_PART 宏會自動為您宣告[AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)、 [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)和[QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))函式，但您仍然需要執行這些功能：

```cpp
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
    REFIID iid,
    void FAR* FAR* ppvObj)
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

CEditPrintObj::CPrintObj 的實作會類似上述 CEditPrintObj::CEditObj 的定義。 雖然有可能建立用來自動產生這些函式的巨集 (但是在稍早的 MFC/OLE 開發中就是這樣的情況)，但是很難在巨集產生一行以上的程式碼時設定中斷點。 基於這個理由，這個程式碼會以手動方式展開。

藉由使用訊息對應的架構實作，有一些不一定需要執行的動作：

- 實作 QueryInterface

- 實作 AddRef 和 Release

- 在兩個介面上宣告其中一種內建方法

此外，架構會在內部使用訊息對應。 這可讓您從架構類別衍生，例如 `COleServerDoc`，已經支援特定介面並提供架構所提供之介面的取代或新增項目。 您可以執行這個動作，因為架構完全支援從基底類別繼承介面對應。 這就是 BEGIN_INTERFACE_MAP 做為其第二個參數的原因，也就是基類的名稱。

> [!NOTE]
> 它通常無法僅藉由從 MFC 版本繼承介面的內嵌特製化，就能重複使用 OLE 介面之 MFC 內建實作的實作。 這是不可能的，因為使用 METHOD_PROLOGUE 宏來取得包含 `CCmdTarget`衍生物件的存取權，意味著已從 `CCmdTarget`衍生的物件中內嵌物件的*固定位移*。 例如，這就表示您無法從 `COleClientItem::XAdviseSink` 中的 MFC 實作衍生內嵌的 XMyAdviseSink，因為 XAdviseSink 依賴位於來自 `COleClientItem` 物件頂端的特定位移。

> [!NOTE]
> 不過，您可以將所有您希望其成為 MFC 預設行為的函式委派給 MFC 實作。 這是 `COleFrameHook` 類別中 `IOleInPlaceFrame` (XOleInPlaceFrame) 的 MFC 實作 (它會將許多函數委派至 m_xOleInPlaceUIWindow)。 選擇此設計可減少實作許多介面之物件的執行階段大小，排除對返回指標的需求 (如前一節中使用的方式 m_pParent)。

### <a name="aggregation-and-interface-maps"></a>彙總與介面對應

除了支援獨立的 COM 物件，MFC 也支援彙總。 匯總本身過於複雜，無法在此討論主題;如需匯總的詳細資訊，請參閱[匯總](/windows/win32/com/aggregation)主題。 這個註解只描述對內建於架構和介面對應中的彙總支援。

有兩種方式來使用彙總：(1) 使用支援彙總的 COM 物件，以及 (2) 實作可由另一個物件彙總的物件。 這些功能可以稱為「使用彙總物件」和「使物件彙總」。 MFC 兩者皆可支援。

### <a name="using-an-aggregate-object"></a>使用彙總物件

若要使用彙總物件，則必須有某種方式將彙總繫結到 QueryInterface 機制。 換句話說，彙總物件的行為必須如同物件的原生組件一般。 因此，除了 INTERFACE_PART 宏之外，這會如何系結至 MFC 的介面對應機制，其中嵌套的物件會對應至 IID，您也可以將匯總物件宣告為 `CCmdTarget` 衍生類別的一部分。 若要這麼做，請使用 INTERFACE_AGGREGATE 宏。 這可讓您指定成員變數（必須是[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)或衍生類別的指標），這會整合到介面對應機制中。 當呼叫 `CCmdTarget::ExternalQueryInterface` 時，如果指標不是 Null，則架構會自動呼叫匯總物件的[QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))成員函式，如果所要求的 `IID` 不是 `CCmdTarget` 物件本身所支援的其中一個原生 `IID`。

#### <a name="to-use-the-interface_aggregate-macro"></a>使用 INTERFACE_AGGREGATE 巨集

1. 宣告成員變數 (`IUnknown*`)，此變數包含指向彙總物件的指標。

2. 在您的介面對應中包含 INTERFACE_AGGREGATE 宏，這會依名稱參考成員變數。

3. 在某個時間點 (通常是在 `CCmdTarget::OnCreateAggregates` 期間)，將成員變數初始化為 NULL 以外的成員變數。

例如：

```cpp
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

m_lpAggrInner 變數會在建構函式中初始化為 NULL。 在預設的[QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))執行中，架構會忽略 Null 成員變數。 `OnCreateAggregates` 是實際建立彙總物件的好地方。 如果您正在建立 `COleObjectFactory` MFC 實作外部的物件，您必須明確地呼叫它。 討論到建立彙總物件時，在 `CCmdTarget::OnCreateAggregates` 中建立彙總和使用 `CCmdTarget::GetControllingUnknown` 的原因將會變得很明確。

這項技術可提供您的物件彙總物件支援的所有介面及其原生介面。 如果您只想要彙總支援介面的子集，您可以覆寫 `CCmdTarget::GetInterfaceHook`。 這可讓您非常低層級的 hookability，類似于[QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))。 您通常會想要彙總支援的所有介面。

### <a name="making-an-object-implementation-aggregatable"></a>讓物件實作可以彙總

若要讓物件成為可匯總的， [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)、 [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)和[QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))的執行必須委派給「控制未知」。 換句話說，若要讓它成為物件的一部分，它必須將[AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)、 [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)和[QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))委派給另一個物件，也就是從[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)衍生而來。 這個 "controlling unknown" 可在建立物建時提供給物件，亦即提供給 `COleObjectFactory` 的實作。 實作此項目會帶來少量的額外負荷，在某些情況下不需要這樣做，因此 MFC 使其為選擇性項目。 若要讓物件彙總，您可以從物件的建構函式呼叫 `CCmdTarget::EnableAggregation`。

如果物件也使用彙總，您也必須確定傳遞正確的 "controlling unknown" 給彙總物件。 當建立匯總時，通常會將此[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)指標傳遞至物件。 例如，pUnkOuter 參數是利用 `CoCreateInstance` 建立之物建的 "controlling unknown"。 正確的 "controlling unknown" 指標可以藉由呼叫 `CCmdTarget::GetControllingUnknown` 擷取。 然而，從函式傳回的值在建構函式期間無效。 基於這個理由，即使是從 `COleObjectFactory` 實作建立彙總，建議您只在 `CCmdTarget::OnCreateAggregates` 的覆寫中建立彙總，其中從 `GetControllingUnknown` 的傳回值是可靠的。

另一個重點是物件在新增或釋放假造的參考計數時會管理正確的參考計數。 若要確保此情況，請務必呼叫 `ExternalAddRef` 和 `ExternalRelease` 而不是 `InternalRelease` 和 `InternalAddRef`。 我們很少在支援彙總的類別上呼叫 `InternalRelease` 或 `InternalAddRef`。

## <a name="reference-material"></a>參考資料

OLE 的進階用法，例如定義您自己的介面或覆寫架構的 OLE 介面實作，需要使用基礎的介面對應機制。

本節討論可用來實作這些進階功能的每個巨集和 API。

### <a name="ccmdtargetenableaggregation--function-description"></a>CCmdTarget::EnableAggregation — 函式描述

```cpp
void EnableAggregation();
```

#### <a name="remarks"></a>備註

如果您想要支援此類型物件的 OLE 彙總，請在衍生類別的建構函式中呼叫此函式。 這會準備可彙總物建所需的特殊 IUnknown 實作。

### <a name="ccmdtargetexternalqueryinterface--function-description"></a>CCmdTarget::ExternalQueryInterface - 函式描述

```cpp
DWORD ExternalQueryInterface(
    const void FAR* lpIID,
    LPVOIDFAR* ppvObj
);
```

#### <a name="parameters"></a>參數

*lpIID*<br/>
指向 IID 的遠端指標 (QueryInterface 的第一個引數)

*ppvObj*<br/>
指向 IUnknown* 的指標 (QueryInterface 的第二個引數)

#### <a name="remarks"></a>備註

在 IUnknown 實作中為類別實作的每個介面呼叫此函式。 此函式會根據物件的介面對應，提供 QueryInterface 的標準資料導向實作。 它是將傳回值轉換為 HRESULT 的必要項。 如果已彙總物件，此函式會呼叫 "controlling IUnknown"，而不是使用本機介面對應。

### <a name="ccmdtargetexternaladdref--function-description"></a>CCmdTarget::ExternalAddRef - 函式描述

```cpp
DWORD ExternalAddRef();
```

#### <a name="remarks"></a>備註

在 IUnknown::AddRef 實作中為類別實作的每個介面呼叫此函式。 傳回值是 CCmdTarget 物件上的新參考計數。 如果已彙總物件，此函式會呼叫 "controlling IUnknown"，而不是管理本機參考計數。

### <a name="ccmdtargetexternalrelease--function-description"></a>CCmdTarget::ExternalRelease - 函式描述

```cpp
DWORD ExternalRelease();
```

#### <a name="remarks"></a>備註

在 IUnknown::Release 實作中為類別實作的每個介面呼叫此函式。 傳回的值表示物件上的新參考計數。 如果已彙總物件，此函式會呼叫 "controlling IUnknown"，而不是管理本機參考計數。

### <a name="declare_interface_map--macro-description"></a>DECLARE_INTERFACE_MAP - 巨集描述

```cpp
DECLARE_INTERFACE_MAP
```

#### <a name="remarks"></a>備註

在衍生自具有介面對應之 `CCmdTarget` 的任何類別中使用這個巨集。 其使用方式與 DECLARE_MESSAGE_MAP 非常類似。 這個巨集引動過程應該放在類別定義中，通常是在標頭 (.H) 檔案中。 具有 DECLARE_INTERFACE_MAP 的類別必須在執行檔（）中定義介面對應。CPP）搭配 BEGIN_INTERFACE_MAP 和 END_INTERFACE_MAP 宏。

### <a name="begin_interface_part-and-end_interface_part--macro-descriptions"></a>BEGIN_INTERFACE_PART 和 END_INTERFACE_PART - 巨集描述

```cpp
BEGIN_INTERFACE_PART(localClass, iface);
END_INTERFACE_PART(localClass)
```

#### <a name="parameters"></a>參數

*localClass*<br/>
實作介面的類別名稱。

*iface*<br/>
這個類別實作的介面名稱。

#### <a name="remarks"></a>備註

針對您的類別將會執行的每個介面，您需要有 BEGIN_INTERFACE_PART 和 END_INTERFACE_PART 組。 這些巨集會定義衍生自您定義之 OLE 介面的本機類別，並且定義該類別的內嵌成員變數。 [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)、 [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)和[QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))成員會自動宣告。 您必須包含其他成員函式的宣告，而這些函式是正在實作為介面的一部分（這些宣告會放在 BEGIN_INTERFACE_PART 和 END_INTERFACE_PART 宏之間）。

*Iface*引數是您想要執行的 OLE 介面，例如 `IAdviseSink`或 `IPersistStorage` （或您自己的自訂介面）。

*LocalClass*引數是將要定義之本機類別的名稱。 ' X' 將會自動加在名稱前面。 此命名慣例用來避免和相同名稱之全域類別的衝突。 此外，內嵌成員的名稱與*localClass*名稱相同，唯一不同之處在于它的前面會加上 ' m_x '。

例如：

```cpp
BEGIN_INTERFACE_PART(MyAdviseSink, IAdviseSink)
    STDMETHOD_(void, OnDataChange)(LPFORMATETC, LPSTGMEDIUM);
    STDMETHOD_(void, OnViewChange)(DWORD, LONG);
    STDMETHOD_(void, OnRename)(LPMONIKER);
    STDMETHOD_(void, OnSave)();
    STDMETHOD_(void, OnClose)();
END_INTERFACE_PART(MyAdviseSink)
```

會定義衍生自 IAdviseSink 且名為 XMyAdviseSink 的本機類別，並定義該類別在其中宣告為 m_xMyAdviseSink.Note 的類別成員：

> [!NOTE]
> 開頭為 `STDMETHOD`_ 的行基本上會從 OLE2 複製。H 並稍微修改。 從 OLE2.H 將其複製可以減少很難解決的錯誤。

### <a name="begin_interface_map-and-end_interface_map--macro-descriptions"></a>BEGIN_INTERFACE_MAP 和 END_INTERFACE_MAP - 巨集描述

```cpp
BEGIN_INTERFACE_MAP(theClass, baseClass)
END_INTERFACE_MAP
```

#### <a name="parameters"></a>參數

*theClass*<br/>
在其中定義介面對應的類別

*baseClass*<br/>
從中衍生*theClass*的類別。

#### <a name="remarks"></a>備註

BEGIN_INTERFACE_MAP 和 END_INTERFACE_MAP 宏會在執行檔中用來實際定義介面對應。 針對每個執行的介面，都有一或多個 INTERFACE_PART 宏調用。 針對類別所使用的每個匯總，有一個 INTERFACE_AGGREGATE 宏調用。

### <a name="interface_part--macro-description"></a>INTERFACE_PART - 巨集描述

```cpp
INTERFACE_PART(theClass, iid, localClass)
```

#### <a name="parameters"></a>參數

*theClass*<br/>
包含介面對應的類別名稱。

*iid*<br/>
要對應到內嵌類別的 `IID`。

*localClass*<br/>
本機類別的名稱 (減去 'X')。

#### <a name="remarks"></a>備註

這個宏會在 BEGIN_INTERFACE_MAP 宏與您的物件將支援的每個介面的 END_INTERFACE_MAP 宏之間使用。 它可讓您將 IID 對應至*theClass*和*localClass*所指示之類別的成員。 ' M_x ' 會自動新增至*localClass* 。 請注意，一個以上的 `IID` 會與單一成員相關聯。 當您只實作「最常衍生的」介面，並且想要提供所有中繼介面時，這會非常實用。 一個良好的範例是 `IOleInPlaceFrameWindow` 介面。 它的階層看起來像這樣：

```Hierarchy
IUnknown
    IOleWindow
        IOleUIWindow
            IOleInPlaceFrameWindow
```

如果物件執行 `IOleInPlaceFrameWindow`，則除了「最常衍生的」介面 `IOleInPlaceFrameWindow` （您實際執行的程式）之外，用戶端可能會在下列任何介面上 `QueryInterface` `IOleUIWindow`、`IOleWindow`或[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)。 若要處理這種情況，您可以使用一個以上的 INTERFACE_PART 宏，將每個基底介面對應至 `IOleInPlaceFrameWindow` 介面：

在類別定義檔中：

```cpp
BEGIN_INTERFACE_PART(CMyFrameWindow, IOleInPlaceFrameWindow)
```

在類別實作檔中：

```cpp
BEGIN_INTERFACE_MAP(CMyWnd, CFrameWnd)
    INTERFACE_PART(CMyWnd, IID_IOleWindow, MyFrameWindow)
    INTERFACE_PART(CMyWnd, IID_IOleUIWindow, MyFrameWindow)
    INTERFACE_PART(CMyWnd, IID_IOleInPlaceFrameWindow, MyFrameWindow)
END_INTERFACE_MAP
```

架構會負責 IUnknown，因為它一律為必要項。

### <a name="interface_part--macro-description"></a>INTERFACE_PART - 巨集描述

```cpp
INTERFACE_AGGREGATE(theClass, theAggr)
```

#### <a name="parameters"></a>參數

*theClass*<br/>
包含介面對應的類別名稱，

*theAggr*<br/>
要彙總的成員變數名稱。

#### <a name="remarks"></a>備註

這個巨集可用來告知架構類別正在使用彙總物件。 它必須出現在 BEGIN_INTERFACE_PART 和 END_INTERFACE_PART 宏之間。 匯總物件是獨立的物件，衍生自[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)。 藉由使用匯總和 INTERFACE_AGGREGATE 宏，您可以讓匯總支援的所有介面都能直接受到物件的支援。 *TheAggr*引數只是衍生自[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) （直接或間接）之類別的成員變數名稱。 當放在介面對應中時，所有 INTERFACE_AGGREGATE 宏都必須遵循 INTERFACE_PART 宏。

## <a name="see-also"></a>請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)

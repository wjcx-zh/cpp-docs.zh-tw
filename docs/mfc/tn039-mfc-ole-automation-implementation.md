---
title: TN039:MFC OLE Automation 實作
ms.date: 06/28/2018
f1_keywords:
- vc.mfc.ole
helpviewer_keywords:
- MFC, COM support
- IDispatch interface
- MFC, OLE DB and
- TN039
- Automation, MFC COM interface entry points
ms.assetid: 765fa3e9-dd54-4f08-9ad2-26e0546ff8b6
ms.openlocfilehash: cd6f8d681ef7e6517f2172ca6b22b13723a962fd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62305485"
---
# <a name="tn039-mfcole-automation-implementation"></a>TN039:MFC/OLE Automation 實作

> [!NOTE]
> 下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

## <a name="overview-of-ole-idispatch-interface"></a>OLE IDispatch 介面的概觀

`IDispatch`介面是由此應用程式會公開方法和屬性，可讓其他應用程式，例如 Visual BASIC 或其他語言，例如使用應用程式的功能的方法。 這個介面的最重要的部分是`IDispatch::Invoke`函式。 MFC 可讓您使用 「 分派對應 」 實作`IDispatch::Invoke`。 分派對應的配置或 「 形狀 」 上提供的 MFC 實作資訊您`CCmdTarget`-使它可以直接操作物件的屬性，或呼叫成員函式，以滿足您物件中的衍生類別， `IDispatch::Invoke`要求。

大部分的情況下，ClassWizard 和 MFC 合作以隱藏大部分的應用程式設計人員從 OLE automation 的詳細資料中。 程式設計人員專注於應用程式中公開 （expose） 的實際功能，並不需要擔心基礎工作留給。

有一些的情況，不過，就必須了解 MFC 進行幕後。 本附註會說明架構如何指派**DISPID**的成員函式和屬性。 MFC 會使用指派之演算法的知識**DISPID**當您需要知道識別碼，例如當您建立 「 型別程式庫 」 您的應用程式物件時，才需要 s。

## <a name="mfc-dispid-assignment"></a>MFC DISPID 指派

自動化的自動化 （Visual Basic 的使用者，例如），使用者會看到的實際名稱雖然啟用屬性和方法 （例如 obj 其程式碼中ShowWindow) 的實作`IDispatch::Invoke`不會收到的實際名稱。 基於最佳化時，它會接收**DISPID**，也就是 32 位元"magic cookie"，描述的方法或屬性存取。 這些**DISPID**會傳回值，從`IDispatch`透過呼叫另一個方法的實作`IDispatch::GetIDsOfNames`。 Automation 用戶端應用程式會呼叫`GetIDsOfNames`想要存取及快取它們，以便稍後呼叫每個成員或屬性後`IDispatch::Invoke`。 如此一來，耗費資源的字串查閱只執行一次每次物件使用，而不是一次每`IDispatch::Invoke`呼叫。

MFC 會決定**DISPID**每個方法的屬性會根據兩件事：

- 從頂端的分派對應 （1 相對） 之間的距離

- 之間距離的分派對應從 (0，而相對) 的最具衍生性類別

**DISPID**分為兩個部分。 **取代 LOWORD**的**DISPID**包含第一個元件，也就是從分派對應頂端的距離。 **HIWORD**包含從最具衍生性的類別之間的距離。 例如: 

```cpp
class CDispPoint : public CCmdTarget
{
public:
    short m_x, m_y;
    // ...
    DECLARE_DISPATCH_MAP()
    // ...
};

class CDisp3DPoint : public CDispPoint
{
public:
    short m_z;
    // ...
    DECLARE_DISPATCH_MAP()
    // ...
};

BEGIN_DISPATCH_MAP(CDispPoint, CCmdTarget)
    DISP_PROPERTY(CDispPoint, "x", m_x, VT_I2)
    DISP_PROPERTY(CDispPoint, "y", m_y, VT_I2)
END_DISPATCH_MAP()

BEGIN_DISPATCH_MAP(CDisp3DPoint, CDispPoint)
    DISP_PROPERTY(CDisp3DPoint, "z", m_z, VT_I2)
END_DISPATCH_MAP()
```

如您所見，有兩個類別，這兩種 OLE automation 介面公開 （expose）。 其中一個類別衍生自其他，因此會利用基底類別的功能，包括 OLE automation 組件 ("x"和"y"屬性在此情況下)。

MFC 會產生**DISPID**s 類別 CDispPoint，如下所示：

```cpp
property X    (DISPID)0x00000001
property Y    (DISPID)0x00000002
```

因為屬性不在基底類別中**HIWORD**的**DISPID**也永遠是的零 （CDispPoint 的最具衍生性類別之間的距離是零）。

MFC 會產生**DISPID**s 類別 CDisp3DPoint，如下所示：

```cpp
property Z    (DISPID)0x00000001
property X    (DISPID)0x00010001
property Y    (DISPID)0x00010002
```

Z 屬性指定**DISPID**零**HIWORD**因為它公開的屬性，CDisp3DPoint 類別中定義。 X 和 Y 屬性會定義在基底類別中，由於**HIWORD**的**DISPID**為 1，因為這些屬性定義的類別是在一個衍生自最具衍生性類別的距離。

> [!NOTE]
> **取代 LOWORD**一律取決於的位置，在對應中，即使有明確的對應中的項目**DISPID** (請參閱下一節的資訊 **_ID**新版`DISP_PROPERTY`和`DISP_FUNCTION`巨集)。

## <a name="advanced-mfc-dispatch-map-features"></a>進階 MFC 分派對應功能

有這一版的 Visual ClassWizard 不支援的其他功能的數字C++。 支援 ClassWizard `DISP_FUNCTION`， `DISP_PROPERTY`，和`DISP_PROPERTY_EX`以定義方法，成員變數的屬性，以及 get/set 成員函式屬性，分別。 這些功能通常只需要建立大部分的 automation 伺服器。

支援的 ClassWizard 巨集不足夠時，就可以使用下列其他巨集： `DISP_PROPERTY_NOTIFY`，和`DISP_PROPERTY_PARAM`。

## <a name="disppropertynotify--macro-description"></a>DISP_PROPERTY_NOTIFY — Macro Description

```cpp
DISP_PROPERTY_NOTIFY(
    theClass,
    pszName,
    memberName,
    pfnAfterSet,
    vtPropType)
```

### <a name="parameters"></a>參數

*theClass*<br/>
類別的名稱。

*pszName*<br/>
屬性外部名稱。

*memberName*<br/>
儲存屬性的成員變數的名稱。

*pfnAfterSet*<br/>
當屬性變更時要呼叫成員函式的名稱。

*vtPropType*<br/>
值，指定屬性的型別。

### <a name="remarks"></a>備註

這個巨集很像 DISP_PROPERTY，不同之處在於它可接受的其他引數。 其他引數*pfnAfterSet，* 應傳回任何值，並不接受任何參數，'void OnPropertyNotify()' 的成員函式。 它會稱為 「**之後**已修改成員變數。

## <a name="disppropertyparam--macro-description"></a>DISP_PROPERTY_PARAM — Macro Description

```cpp
DISP_PROPERTY_PARAM(
    theClass,
    pszName,
    pfnGet,
    pfnSet,
    vtPropType,
    vtsParams)
```

### <a name="parameters"></a>參數

*theClass*<br/>
類別的名稱。

*pszName*<br/>
屬性外部名稱。

*memberGet*<br/>
用來取得屬性的成員函式的名稱。

*memberSet*<br/>
用來設定屬性的成員函式的名稱。

*vtPropType*<br/>
值，指定屬性的型別。

*vtsParams*<br/>
空間的字串會分隔 VTS_，每個參數。

### <a name="remarks"></a>備註

更像 DISP_PROPERTY_EX 巨集，這個巨集會定義使用個別的 Get 和 Set 成員函式存取的屬性。 不過，這個巨集，可讓您指定之屬性的參數清單。 這是適合用來實作以其他方式的屬性編製索引或參數化。 參數永遠都會放在第一次，後面接著新屬性的值。 例如: 

```cpp
DISP_PROPERTY_PARAM(CMyObject, "item", GetItem, SetItem, VT_DISPATCH, VTS_I2 VTS_I2)
```

就會對應至 get 和 set 成員函式：

```cpp
LPDISPATCH CMyObject::GetItem(short row, short col)
void CMyObject::SetItem(short row, short col, LPDISPATCH newValue)
```

## <a name="dispxxxxid--macro-descriptions"></a>DISP_XXXX_ID — 巨集描述

```cpp
DISP_FUNCTION_ID(
    theClass,
    pszName,
    dispid,
    pfnMember,
    vtRetVal,
    vtsParams)
DISP_PROPERTY_ID(
    theClass,
    pszName,
    dispid,
    memberName,
    vtPropType)
DISP_PROPERTY_NOTIFY_ID(
    theClass,
    pszName,
    dispid,
    memberName,
    pfnAfterSet,
    vtPropType)
DISP_PROPERTY_EX_ID(
    theClass,
    pszName,
    dispid,
    pfnGet,
    pfnSet,
    vtPropType)
DISP_PROPERTY_PARAM_ID(
    theClass,
    pszName,
    dispid,
    pfnGet,
    pfnSet,
    vtPropType,
    vtsParams)
```

### <a name="parameters"></a>參數

*theClass*<br/>
類別的名稱。

*pszName*<br/>
屬性外部名稱。

*dispid*<br/>
固定的 DISPID，屬性或方法。

*pfnGet*<br/>
用來取得屬性的成員函式的名稱。

*pfnSet*<br/>
用來設定屬性的成員函式的名稱。

*memberName*<br/>
若要將對應至屬性的成員變數的名稱

*vtPropType*<br/>
值，指定屬性的型別。

*vtsParams*<br/>
空間的字串會分隔 VTS_，每個參數。

### <a name="remarks"></a>備註

這些巨集可讓您指定**DISPID**而不是讓 MFC 會自動指派使用者帳戶。 這些進階巨集具有相同的名稱，但該識別碼會附加至巨集名稱 (例如**DISP_PROPERTY_ID**) 和識別碼由後面指定的參數*pszName*參數。 請參閱 AFXDISP。如需有關這些巨集 H。 **_ID**項目必須放置在分派對應的結尾。 它們會影響自動**DISPID**為非相同的方式產生 **_ID**巨集的版本會 ( **DISPID**s 取決於位置)。 例如: 

```cpp
BEGIN_DISPATCH_MAP(CDisp3DPoint, CCmdTarget)
    DISP_PROPERTY(CDisp3DPoint, "y", m_y, VT_I2)
    DISP_PROPERTY(CDisp3DPoint, "z", m_z, VT_I2)
    DISP_PROPERTY_ID(CDisp3DPoint, "x", 0x00020003, m_x, VT_I2)
END_DISPATCH_MAP()
```

MFC 會產生 Dispid CDisp3DPoint 類別，如下所示：

```cpp
property X    (DISPID)0x00020003
property Y    (DISPID)0x00000002
property Z    (DISPID)0x00000001
```

指定固定**DISPID**適合用來維護回溯相容性的先前已存在的分派介面，或實作特定的系統定義的方法或屬性 (通常由負**DISPID**，這類**DISPID_NEWENUM**集合)。

## <a name="retrieving-the-idispatch-interface-for-a-coleclientitem"></a>擷取 COleClientItem IDispatch 介面

許多伺服器將支援在其文件物件，以及 OLE 伺服器功能的自動化。 若要存取此自動化介面，就必須直接存取`COleClientItem::m_lpObject`成員變數。 下列程式碼會擷取`IDispatch`介面的物件衍生自`COleClientItem`。 如果您發現這項功能所需，您可以在您的應用程式中包含下列程式碼：

```cpp
LPDISPATCH CMyClientItem::GetIDispatch()
{
    ASSERT_VALID(this);
    ASSERT(m_lpObject != NULL);

    LPUNKNOWN lpUnk = m_lpObject;

    Run();      // must be running

    LPOLELINK lpOleLink = NULL;
    if (m_lpObject->QueryInterface(IID_IOleLink,
        (LPVOID FAR*)&lpOleLink) == NOERROR)
    {
        ASSERT(lpOleLink != NULL);
        lpUnk = NULL;
        if (lpOleLink->GetBoundSource(&lpUnk) != NOERROR)
        {
            TRACE0("Warning: Link is not connected!\n");
            lpOleLink->Release();
            return NULL;
        }
        ASSERT(lpUnk != NULL);
    }

    LPDISPATCH lpDispatch = NULL;
    if (lpUnk->QueryInterface(IID_IDispatch, &lpDispatch) != NOERROR)
    {
        TRACE0("Warning: does not support IDispatch!\n");
        return NULL;
    }

    ASSERT(lpDispatch != NULL);
    return lpDispatch;
}
```

分派介面傳回此函式無法再直接使用或附加至`COleDispatchDriver`型別安全存取。 如果您直接使用它，請確定您呼叫其`Release`成員時透過指標 (`COleDispatchDriver`解構函式的做法是預設值)。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)

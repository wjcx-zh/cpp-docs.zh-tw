---
title: 'TN039: MFC OLE Automation 實作 |Microsoft 文件'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.ole
dev_langs:
- C++
helpviewer_keywords:
- MFC, COM support
- IDispatch interface
- MFC, OLE DB and
- TN039
- Automation, MFC COM interface entry points
ms.assetid: 765fa3e9-dd54-4f08-9ad2-26e0546ff8b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9dcc179b1481c4f1f6b6a0773bba792eefffae25
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122117"
---
# <a name="tn039-mfcole-automation-implementation"></a>TN039：MFC/OLE Automation 實作

> [!NOTE]
> 下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

## <a name="overview-of-ole-idispatch-interface"></a>OLE IDispatch 介面的概觀

`IDispatch`介面是由其應用程式會公開方法和屬性，可讓其他應用程式，例如 Visual BASIC 或其他語言，例如使用的應用程式的功能的方式。 這個介面的最重要的部分是`IDispatch::Invoke`函式。 MFC 會使用 「 分派對應 」 實作`IDispatch::Invoke`。 分派對應提供的 MFC 實作資訊的配置或"shape"的程式`CCmdTarget`-衍生的類別，使它可以直接操作物件的屬性或呼叫成員函式，以滿足您物件內`IDispatch::Invoke`要求。

大部分的情況下，ClassWizard 和 MFC 合作以隱藏大部分的應用程式設計來自 OLE automation 的詳細資料。 程式設計人員專注於應用程式中公開的實際功能，而且不需要擔心基礎配管。

有些情況是，不過，就必須了解 MFC 進行幕後。 此提示會說明架構如何指派**DISPID**的成員函式和屬性。 MFC 會使用指派的演算法知識**DISPID**s 時，才需要時想要知道識別碼，例如當您建立 「 型別程式庫 」 您的應用程式物件。

## <a name="mfc-dispid-assignment"></a>MFC DISPID 指派

屬性和方法 （例如 obj 標定程式碼中的，雖然自動化 （Visual Basic 的使用者，例如），使用者會看到的實際名稱啟用自動化ShowWindow) 的實作`IDispatch::Invoke`不會收到的實際名稱。 為了最佳化時，它會接收**DISPID**，即 32 位元"magic cookie"，描述的方法或存取的屬性。 這些**DISPID**值會傳回從`IDispatch`透過呼叫另一個方法的實作`IDispatch::GetIDsOfNames`。 Automation 用戶端應用程式會呼叫`GetIDsOfNames`之後每個成員或屬性對於要存取，並快取它們，以便稍後呼叫`IDispatch::Invoke`。 如此一來，高度耗費資源的字串查閱只執行一次每次物件使用，而不是一次每個`IDispatch::Invoke`呼叫。

MFC 判斷**DISPID**每個方法的屬性會根據兩件事：

- 從頂端的分派對應 （1 相對的） 之間的距離

- 距離，從最常衍生的類別 (相對 0) 的分派對應

**DISPID**分成兩個部分。 **取代 LOWORD**的**DISPID**包含第一個元件，也就是分派對應頂端之間的距離。 **HIWORD**包含最常衍生的類別之間的距離。 例如: 

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

如您所見，有兩種類別，這兩種公開 OLE automation 介面。 這些類別的其中一個衍生自另，並因此可運用基底類別的功能，包括 OLE automation 組件 ("x"和"y"屬性，在此情況下)。

MFC 會產生**DISPID**s 類別 CDispPoint，如下所示：

```cpp
property X    (DISPID)0x00000001
property Y    (DISPID)0x00000002
```

因為屬性不是基底類別， **HIWORD**的**DISPID**也永遠是的零 （如 CDispPoint 最常衍生的類別之間的距離是零）。

MFC 會產生**DISPID**s 類別 CDisp3DPoint，如下所示：

```cpp
property Z    (DISPID)0x00000001
property X    (DISPID)0x00010001
property Y    (DISPID)0x00010002
```

Z 屬性指定**DISPID**具有零**HIWORD**因為它定義在所公開的屬性，CDisp3DPoint 類別。 因為基底類別中定義的 X 及 Y 屬性**HIWORD**的**DISPID**為 1，因為這些屬性定義的類別是在最常衍生的類別衍生一個距離。

> [!NOTE]
> **取代 LOWORD**一律取決於的位置，在對應中，即使有明確的對應中的項目**DISPID** (請參閱下一節的資訊 **_ID**新版`DISP_PROPERTY`和`DISP_FUNCTION`巨集)。

## <a name="advanced-mfc-dispatch-map-features"></a>進階 MFC 分派對應功能

有這一版的 Visual c + + 類別精靈不支援的額外功能的數字。 ClassWizard 支援`DISP_FUNCTION`， `DISP_PROPERTY`，和`DISP_PROPERTY_EX`來定義方法，成員變數的屬性，並取得/設定成員函式屬性，分別。 這些功能通常只需要建立大部分的 automation 伺服程式。

支援的 ClassWizard 巨集不是適當時，就可以使用下列其他巨集： `DISP_PROPERTY_NOTIFY`，和`DISP_PROPERTY_PARAM`。

## <a name="disppropertynotify--macro-description"></a>DISP_PROPERTY_NOTIFY — 巨集描述

```cpp
DISP_PROPERTY_NOTIFY(
    theClass,
    pszName,
    memberName,
    pfnAfterSet,
    vtPropType)
```

### <a name="parameters"></a>參數

*theClass*  
 類別的名稱。

*pszName*  
 屬性外部名稱。

*成員名稱*  
 成員變數中儲存之屬性的名稱。

*pfnAfterSet*  
 屬性變更時要呼叫成員函式的名稱。

*vtPropType*  
 值，指定屬性的型別。

### <a name="remarks"></a>備註

這個巨集就像 DISP_PROPERTY，不同之處在於它可接受的其他引數。 其他引數， *pfnAfterSet，* 應傳回任何項目並不採用任何參數 'void OnPropertyNotify()' 的成員函式。 將呼叫**之後**成員變數已被修改。

## <a name="disppropertyparam--macro-description"></a>DISP_PROPERTY_PARAM — 巨集描述

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

*theClass*  
 類別的名稱。

*pszName*  
 屬性外部名稱。

*memberGet*  
 用來取得屬性的成員函式的名稱。

*成員集合*  
 用來設定屬性的成員函式的名稱。

*vtPropType*  
 值，指定屬性的型別。

*vtsParams*  
 空間的字串以 VTS_ 分隔每個參數。

### <a name="remarks"></a>備註

更像 DISP_PROPERTY_EX 巨集，此巨集定義屬性，使用個別的 Get 和 Set 成員函式存取。 不過，這個巨集，可讓您指定之屬性的參數清單。 這是適用於其他方法實作會編製索引或參數化的屬性。 參數永遠都會放在第一次，後面接著新屬性的值。 例如: 

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

*theClass*  
類別的名稱。

*pszName*  
屬性外部名稱。

*dispid*  
固定的屬性或方法的 DISPID。

*pfnGet*  
用來取得屬性的成員函式的名稱。

*pfnSet*  
用來設定屬性的成員函式的名稱。

*成員名稱*  
成員變數，將對應至屬性的名稱

*vtPropType*  
值，指定屬性的型別。

*vtsParams*  
空間的字串以 VTS_ 分隔每個參數。

### <a name="remarks"></a>備註

這些巨集可讓您指定**DISPID**而非讓 MFC 自動指派。 這些進階巨集具有相同的名稱，但該識別碼會附加至巨集名稱 (例如**DISP_PROPERTY_ID**) 和識別碼由參數之後指定*pszName*參數。 請參閱 AFXDISP。如需有關這些巨集 H。 **_ID**項目必須放在分派對應的結尾。 它們會影響自動**DISPID**中與非相同的方式產生 **_ID**巨集版本會 ( **DISPID**s 取決於位置)。 例如: 

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

指定固定**DISPID**可用以維護回溯相容性的先前已存在的分派介面，或實作特定系統定義的方法或屬性 (通常由負**DISPID**，例如**DISPID_NEWENUM**集合)。

## <a name="retrieving-the-idispatch-interface-for-a-coleclientitem"></a>擷取 COleClientItem IDispatch 介面

許多伺服器將會支援自動化在其文件物件連同 OLE 伺服器功能。 若要存取此 automation 介面，則必須直接存取`COleClientItem::m_lpObject`成員變數。 下列程式碼會擷取`IDispatch`介面物件衍生自`COleClientItem`。 如果您發現這項功能需要，您可以在應用程式中包含下列程式碼：

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

分派介面傳回的這個函式無法再直接使用或附加至`COleDispatchDriver`型別安全存取。 如果您直接使用它，請確定您呼叫其`Release`成員時透過指標 (`COleDispatchDriver`解構函式會依預設)。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)  
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)  

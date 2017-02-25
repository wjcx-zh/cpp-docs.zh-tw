---
title: "TN039：MFC/OLE Automation 實作 | Microsoft Docs"
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
  - "Automation, MFC COM 介面進入點"
  - "IDispatch 介面"
  - "MFC, COM 支援"
  - "MFC, OLE DB 和"
  - "TN039"
ms.assetid: 765fa3e9-dd54-4f08-9ad2-26e0546ff8b6
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# TN039：MFC/OLE Automation 實作
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。  因此，有些程序和主題可能已過期或不正確。  如需最新資訊，建議您在線上文件索引中搜尋相關的主題。  
  
## OLE IDispatch 介面概觀  
 `IDispatch` 介面是應用程式所公開的方法和屬性這類方法的其他應用程式 \(例如 Visual Basic，或其他語言，可以利用應用程式的功能。\)  這個介面的重點是 **IDispatch::Invoke** 函式。  MFC 使用「分派對應」實作 **IDispatch::Invoke**。  分派對應在配置或形狀提供 MFC 實作資訊至 `CCmdTarget`衍生類別，這樣它可以直接操作物件的屬性，或呼叫物件內的成員函式符合 **IDispatch::Invoke** 要求。  
  
 在大部分的情況下， ClassWizard 和 MFC 合作隱藏大多 OLE Automation 的詳細資料從應用程式設計工具中。  程式設計人員在應用程式中這種實際功能公開，而且不必擔心這個基本的配管。  
  
 不過，在某些情況下，其中了解需要何種 MFC 在幕後執行的動作。  這個附註處理架構如何指派 **DISPID**的對成員函式和屬性。  演算法使用 MFC 的知識指派的 **DISPID**s 才是必要的，當您需要知道 ID 時，例如，當您建置應用程式的物件有一個型別程式庫」。  
  
## MFC DISPID 指派。  
 雖然 Automation \(例如 Visual Basic 使用者使用者，\)，以自動化允許屬性的實際名稱和方法會將程式碼 \(例如\)， obj.ShowWindow **IDispatch::Invoke** 的實作不會實際名稱。  對於最佳化因素，它接收 **DISPID**，是 32 位元「投影片 Cookie\> 描述方法或屬性的存取。  這些 **DISPID** 值從 `IDispatch` 實作會傳回透過另一個方法，呼叫 **IDispatch::GetIDsOfNames**。  Automation 用戶端應用程式為稍後呼叫一次將呼叫它要存取的每個 `GetIDsOfNames` 成員或屬性，並快取到 **IDispatch::Invoke**。  如此一來，高度耗費資源的字串搜尋一次每個物件只能使用，而不是一次 **IDispatch::Invoke** 呼叫。  
  
 MFC 判斷根據兩個項目和屬性的 **DISPID**的每一個方法:  
  
-   從分派對應 \(1 個相對\) 上方的距離。  
  
-   分派對應的距離大部分衍生類別 \(0 個相對\)  
  
 **DISPID** 分為兩部分。  **DISPID** 的 **LOWORD** 包含第一個元件，從分派對應頂端的距離。  **HIWORD** 包含大部分衍生類別的距離。  例如：  
  
```  
class CDispPoint : public CCmdTarget  
{  
public:  
    short m_x, m_y;  
    ...  
    DECLARE_DISPATCH_MAP()  
    ...  
};  
  
class CDisp3DPoint : public CDispPoint  
{  
public:  
    short m_z;  
    ...  
    DECLARE_DISPATCH_MAP()  
    ...  
};  
  
BEGIN_DISPATCH_MAP(CDispPoint, CCmdTarget)  
    DISP_PROPERTY(CDispPoint, "x", m_x, VT_I2)  
    DISP_PROPERTY(CDispPoint, "y", m_y, VT_I2)  
END_DISPATCH_MAP()  
  
BEGIN_DISPATCH_MAP(CDisp3DPoint, CDispPoint)  
    DISP_PROPERTY(CDisp3DPoint, "z", m_z, VT_I2)  
END_DISPATCH_MAP()  
```  
  
 如您所見，有兩個類別，這兩個公開 OLE Automation 介面。  其中一個類別從其他衍生並因而支援基底類別的功能，包括 OLE Automation 組件 \(「x」和「Y」屬性在這個案例中\)。  
  
 MFC 會產生類別的 CDispPoint **DISPID**s 如下:  
  
```  
property X    (DISPID)0x00000001  
property Y    (DISPID)0x00000002  
```  
  
 因為屬性不是基底類別， **DISPID** 的 **HIWORD** 永遠為零 \(從大部分衍生類別的距離 CDispPoint 為零\)。  
  
 MFC 會產生類別的 CDisp3DPoint **DISPID**s 如下:  
  
```  
property Z    (DISPID)0x00000001  
property X    (DISPID)0x00010001  
property Y    (DISPID)0x00010002  
```  
  
 給 Z 屬性 **DISPID** 和 **HIWORD** 零的，因為它在公開屬性的類別， CDisp3DPoint 定義。  從 X 和 Y 屬性在基底類別中定義， **DISPID** 的 **HIWORD** 是 1，這些屬性定義在遠端處理大部分衍生類別的一個衍生的類別。  
  
> [!NOTE]
>  **LOWORD** 一律取決於對應的位置，因此，即使其中對應中的現有型別與明確 **DISPID** \(請參閱下一節中有關 `DISP_PROPERTY` 和 `DISP_FUNCTION` 巨集的 **\_ID** 版本的資訊\)。  
  
## 進階 MFC 分派對應功能  
 有 ClassWizard 不支援與 Visual C\+\+ 這個版本的許多其他功能。  ClassWizard 分別支援定義方法、成員變數的屬性和取得\/設定成員函式屬性的 `DISP_FUNCTION`、 `DISP_PROPERTY`和 `DISP_PROPERTY_EX` 。  這些功能通常是需要建立大部分自動化伺服器的所有。  
  
 下列巨集，當 ClassWizard 支援的巨集未滿時，可以使用: `DISP_PROPERTY_NOTIFY`和 `DISP_PROPERTY_PARAM`。  
  
## DISP\_PROPERTY\_NOTIFY —描述巨集  
  
```  
  
        DISP_PROPERTY_NOTIFY(   
   theClass,   
   pszName,   
   memberName,   
   pfnAfterSet,   
   vtPropType   
)  
```  
  
## 備註  
  
### 參數  
 `theClass`  
 類別的名稱。  
  
 `pszName`  
 屬性的外部名稱。  
  
 `memberName`  
 屬性儲存成員變數的名稱。  
  
 `pfnAfterSet`  
 成員函式的呼叫時的變更屬性。  
  
 `vtPropType`  
 指定屬性型別的值。  
  
## 備註  
 這個巨集就很像 `DISP_PROPERTY`，不過，它接受其他引數。  其他引數，如*pfnAfterSet,* 應該會傳回而不使用參數的成員函式,void OnPropertyNotify\(\)。  **，在** 修改後，它會呼叫成員變數。  
  
## DISP\_PROPERTY\_PARAM —描述巨集  
  
```  
  
        DISP_PROPERTY_PARAM(   
   theClass,  
   pszName,  
   pfnGet,  
   pfnSet,  
   vtPropType,  
   vtsParams   
)  
```  
  
## 備註  
  
### 參數  
 `theClass`  
 類別的名稱。  
  
 `pszName`  
 屬性的外部名稱。  
  
 `memberGet`  
 這個成員函數的名稱以取得屬性。  
  
 `memberSet`  
 這個成員函數的名稱以設定屬性。  
  
 `vtPropType`  
 指定屬性型別的值。  
  
 `vtsParams`  
 空間字串分隔每個參數的 VTS\_。  
  
## 備註  
 很像 `DISP_PROPERTY_EX` 巨集，這個巨集定義屬性存取使用個別的 Get 和成員函式。  不過這個巨集可讓您指定屬性的參數清單。  這在實作索引或參數化用其他方式的屬性非常有用。  參數將由屬性的新值會先固定位置，再呼叫。  例如：  
  
```  
DISP_PROPERTY_PARAM(CMyObject, "item", GetItem, SetItem, VT_DISPATCH,    VTS_I2 VTS_I2)  
```  
  
 將對應取得和設定成員函式:  
  
```  
LPDISPATCH CMyObject::GetItem(short row, short col)  
void CMyObject::SetItem(short row, short col, LPDISPATCH newValue)  
```  
  
## DISP\_XXXX\_ID—描述巨集  
  
```  
  
        DISP_FUNCTION_ID(   
   theClass,  
   pszName,  
   dispid,  
   pfnMember,  
   vtRetVal,  
   vtsParams   
) DISP_PROPERTY_ID(   
   theClass,  
   pszName,  
   dispid,  
   memberName,  
   vtPropType   
) DISP_PROPERTY_NOTIFY_ID(   
   theClass,  
   pszName,  
   dispid,  
   memberName,  
   pfnAfterSet,  
   vtPropType   
) DISP_PROPERTY_EX_ID(   
   theClass,  
   pszName,  
   dispid,  
   pfnGet,  
   pfnSet,  
   vtPropType   
) DISP_PROPERTY_PARAM_ID(   
   theClass,  
   pszName,  
   dispid,  
   pfnGet,  
   pfnSet,  
   vtPropType,  
   vtsParams   
)  
```  
  
## 備註  
  
### 參數  
 `theClass`  
 類別的名稱。  
  
 `pszName`  
 屬性的外部名稱。  
  
 `dispid`  
 屬性或方法的固定的 DISPID。  
  
 `pfnGet`  
 這個成員函數的名稱以取得屬性。  
  
 `pfnSet`  
 這個成員函數的名稱以設定屬性。  
  
 `memberName`  
 對應的成員變數的名稱屬性。  
  
 `vtPropType`  
 指定屬性型別的值。  
  
 `vtsParams`  
 空間字串分隔每個參數的 VTS\_。  
  
## 備註  
 這些巨集可讓您指定 **DISPID** 而不是讓 MFC 自動指派一個。  這些進階巨集有相同名稱，除了 ID 附加到巨集名稱 \(也就是。  在 `pszName` 參數之後指定之參數所決定**DISP\_PROPERTY\_ID**\) 和 ID。  如需 AFXDISP.H 有關這些巨集的詳細資訊。  必須將 **\_ID** 輸入在分派對應的結尾。  它們會影響 **DISPID** 自動產生，以與巨集的非**\_ID** 版本會類似的方式 \(位置取決於 **DISPID**\)。  例如：  
  
```  
BEGIN_DISPATCH_MAP(CDisp3DPoint, CCmdTarget)  
    DISP_PROPERTY(CDisp3DPoint, "y", m_y, VT_I2)  
    DISP_PROPERTY(CDisp3DPoint, "z", m_z, VT_I2)  
    DISP_PROPERTY_ID(CDisp3DPoint, "x", 0x00020003, m_x, VT_I2)  
END_DISPATCH_MAP()  
```  
  
 MFC 會產生類別的 CDisp3DPoint DISPIDs 如下:  
  
```  
property X    (DISPID)0x00020003  
property Y    (DISPID)0x00000002  
property Z     (DISPID)0x00000001  
```  
  
 指定內建的 **DISPID** 有助於維持回溯相容性至之前存在的分派介面，或是繫結至實作某些系統定義方法或屬性 \(通常以負數 **DISPID**，例如 **DISPID\_NEWENUM** 集合\)。  
  
#### 擷取 COleClientItem 的 IDispatch 介面  
 許多伺服器與 OLE 伺服器功能一起支援其資料物件內的自動化，。  為了這個 Automation 介面存取權，直接存取 **COleClientItem::m\_lpObject** 成員變數是必要的。  下列程式碼會擷取從 `COleClientItem`衍生之物件的 `IDispatch` 介面。  如果您發現這項功能，您必須在應用程式中加入下列程式碼:  
  
```  
LPDISPATCH CMyClientItem::GetIDispatch()  
{  
    ASSERT_VALID(this);  
    ASSERT(m_lpObject != NULL);  
  
    LPUNKNOWN lpUnk = m_lpObject;  
  
    Run();    // must be running  
  
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
    if (lpUnk->QueryInterface(IID_IDispatch, &lpDispatch)   
        != NOERROR)  
    {  
        TRACE0("Warning: does not support IDispatch!\n");  
        return NULL;  
    }  
  
    ASSERT(lpDispatch != NULL);  
    return lpDispatch;  
}  
```  
  
 然後可以直接使用這個函式傳回的分派介面或附加至 `COleDispatchDriver` 為型別安全存取。  如果直接使用它，請確定您將具有指標時呼叫其 **Release** 成員時，根據預設 \( `COleDispatchDriver` 解構這麼做\)。  
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)
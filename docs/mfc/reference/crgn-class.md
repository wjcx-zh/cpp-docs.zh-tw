---
title: "CRgn 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CRgn"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "HRGN"
  - "CRgn 類別"
  - "MFC 的區域"
ms.assetid: d904da84-76aa-481e-8780-b09485f49e64
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRgn 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封裝 Windows 繪圖裝置介面 (GDI) 區域。  
  
## <a name="syntax"></a>語法  
  
```  
class CRgn : public CGdiObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CRgn::CRgn](#crgn__crgn)|建構 `CRgn` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CRgn::CombineRgn](#crgn__combinergn)|設定 `CRgn` 物件，讓它相當於兩個指定的聯集 `CRgn` 物件。|  
|[CRgn::CopyRgn](#crgn__copyrgn)|設定 `CRgn` 物件，使它是一份指定 `CRgn` 物件。|  
|[CRgn::CreateEllipticRgn](#crgn__createellipticrgn)|初始化 `CRgn` 橢圓形的區域物件。|  
|[CRgn::CreateEllipticRgnIndirect](#crgn__createellipticrgnindirect)|初始化 `CRgn` 物件所定義的橢圓形區域 [RECT](../../mfc/reference/rect-structure1.md) 結構。|  
|[CRgn::CreateFromData](#crgn__createfromdata)|從指定的區域和轉換資料，請建立區域。|  
|[CRgn::CreateFromPath](#crgn__createfrompath)|從所選入指定的裝置內容的路徑建立區域。|  
|[CRgn::CreatePolygonRgn](#crgn__createpolygonrgn)|初始化 `CRgn` 多邊形的區域物件。 系統多邊形會自動關閉，必要時，所繪製一條線從最後一個頂點，第一個。|  
|[CRgn::CreatePolyPolygonRgn](#crgn__createpolypolygonrgn)|初始化 `CRgn` 物件組成的一系列的封閉的多邊形的區域。 多邊形可能不相鄰，或可能會重疊。|  
|[CRgn::CreateRectRgn](#crgn__createrectrgn)|初始化 `CRgn` 物件的矩形區域。|  
|[CRgn::CreateRectRgnIndirect](#crgn__createrectrgnindirect)|初始化 `CRgn` 物件所定義的矩形區域 [RECT](../../mfc/reference/rect-structure1.md) 結構。|  
|[CRgn::CreateRoundRectRgn](#crgn__createroundrectrgn)|初始化 `CRgn` 與具有圓角矩形區域的物件。|  
|[CRgn::EqualRgn](#crgn__equalrgn)|檢查兩個 `CRgn` 物件，判斷它們是否相等。|  
|[CRgn::FromHandle](#crgn__fromhandle)|若要將指標傳回 `CRgn` 物件控制代碼給 Windows 區域時。|  
|[CRgn::GetRegionData](#crgn__getregiondata)|指定的緩衝區中填入描述特定的區域的資料。|  
|[CRgn::GetRgnBox](#crgn__getrgnbox)|擷取週框的座標 `CRgn` 物件。|  
|[CRgn::OffsetRgn](#crgn__offsetrgn)|移動 `CRgn` 物件所指定的位移。|  
|[CRgn::PtInRegion](#crgn__ptinregion)|判斷指定的點是否在區域中。|  
|[CRgn::RectInRegion](#crgn__rectinregion)|判斷指定的任何的矩形部分是否為區域的界限內。|  
|[CRgn::SetRectRgn](#crgn__setrectrgn)|設定 `CRgn` 到指定的矩形區域的物件。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CRgn::operator HRGN](#crgn__operator_hrgn)|傳回包含在 Windows 控制代碼 `CRgn` 物件。|  
  
## <a name="remarks"></a>備註  
 區域是在視窗內的橢圓形或多邊形區域。 若要使用的區域，您可以使用類別的成員函式 `CRgn` 與裁剪函式定義為類別成員 `CDC`。  
  
 成員函式 `CRgn` 建立、 改變和擷取的呼叫它們的區域物件的相關資訊。  
  
 如需有關使用 `CRgn`, ，請參閱 [圖形物件](../../mfc/graphic-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CRgn`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="a-namecrgncombinergna-crgncombinergn"></a><a name="crgn__combinergn"></a>  CRgn::CombineRgn  
 建立新的 GDI 區域結合兩個現有的區域。  
  
```  
int CombineRgn(
    CRgn* pRgn1,  
    CRgn* pRgn2,  
    int nCombineMode);
```  
  
### <a name="parameters"></a>參數  
 `pRgn1`  
 識別現有的區域。  
  
 `pRgn2`  
 識別現有的區域。  
  
 `nCombineMode`  
 指定要結合兩個來源區域時執行的作業。 它可以是下列值之一︰  
  
- **RGN_AND** 使用重疊的區域 （交集） 這兩個區域。  
  
- **RGN_COPY** 建立 1 個區域的複本 (由 `pRgn1`)。  
  
- **RGN_DIFF** 建立區域，其中包含 1 個區域的區域 (由 `pRgn1`)，不是 2 個區域的一部分 (由 `pRgn2`)。  
  
- **RGN_OR** 結合完整 （聯集） 這兩個區域。  
  
- **RGN_XOR** 結合這兩個區域，但是移除重疊的區域。  
  
### <a name="return-value"></a>傳回值  
 指定產生的區域類型。 它可以是下列值之一︰  
  
- **COMPLEXREGION** 新區域有重疊的框線。  
  
- **錯誤** 建立任何新的區域。  
  
- **NULLREGION** 新的區域是空的。  
  
- **SIMPLEREGION** 新的區域有沒有重疊的框線。  
  
### <a name="remarks"></a>備註  
 區域的組合所指定 `nCombineMode`。  
  
 兩個指定的區域組合，而產生的區域控制代碼會儲存在 `CRgn` 物件。 因此，任何區域儲存在 `CRgn` 結合區域所取代的物件。  
  
 區域的大小限制為 32767 的 32767 的邏輯單元或 64k 的記憶體，小者為準。  
  
 使用 [CopyRgn](#crgn__copyrgn) 直接將某個區域複製到另一個區域。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#144](../../mfc/codesnippet/CPP/crgn-class_1.cpp)]  
  
##  <a name="a-namecrgncopyrgna-crgncopyrgn"></a><a name="crgn__copyrgn"></a>  CRgn::CopyRgn  
 複製所定義之區域 `pRgnSrc` 到 `CRgn` 物件。  
  
```  
int CopyRgn(CRgn* pRgnSrc);
```  
  
### <a name="parameters"></a>參數  
 `pRgnSrc`  
 識別現有的區域。  
  
### <a name="return-value"></a>傳回值  
 指定產生的區域類型。 它可以是下列值之一︰  
  
- **COMPLEXREGION** 新區域有重疊的框線。  
  
- **錯誤** 建立任何新的區域。  
  
- **NULLREGION** 新的區域是空的。  
  
- **SIMPLEREGION** 新的區域有沒有重疊的框線。  
  
### <a name="remarks"></a>備註  
 新的區域會取代先前儲存在區域 `CRgn` 物件。 此函式是特殊形式的 [CombineRgn](#crgn__combinergn) 成員函式。  
  
### <a name="example"></a>範例  
  請參閱範例 [CRgn::CreateEllipticRgn](#crgn__createellipticrgn)。  
  
##  <a name="a-namecrgncreateellipticrgna-crgncreateellipticrgn"></a><a name="crgn__createellipticrgn"></a>  CRgn::CreateEllipticRgn  
 建立橢圓的區域。  
  
```  
BOOL CreateEllipticRgn(
    int x1,  
    int y1,  
    int x2,  
    int y2);
```  
  
### <a name="parameters"></a>參數  
 `x1`  
 指定邏輯橢圓形的周框矩形左上角的 x 座標。  
  
 `y1`  
 指定的橢圓形的周框矩形的左上角的邏輯 y 座標。  
  
 `x2`  
 指定邏輯橢圓形的周框矩形右下角的 x 座標。  
  
 `y2`  
 指定的橢圓形的周框矩形右下角的邏輯 y 座標。  
  
### <a name="return-value"></a>傳回值  
 如果作業成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 所指定的周框所定義之區域 `x1`, ，`y1`, ，`x2`, ，和 `y2`。 區域儲存在 `CRgn` 物件。  
  
 區域的大小限制為 32767 的 32767 的邏輯單元或 64k 的記憶體，小者為準。  
  
 當它已完成使用區域，以建立 `CreateEllipticRgn` 函式，應用程式應該選取的裝置內容和使用的區域出 `DeleteObject` 函式，將它移除。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#145](../../mfc/codesnippet/CPP/crgn-class_2.cpp)]  
  
##  <a name="a-namecrgncreateellipticrgnindirecta-crgncreateellipticrgnindirect"></a><a name="crgn__createellipticrgnindirect"></a>  CRgn::CreateEllipticRgnIndirect  
 建立橢圓的區域。  
  
```  
BOOL CreateEllipticRgnIndirect(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>參數  
 `lpRect`  
 指向 `RECT` 結構或 `CRect` 物件，其中包含邏輯橢圓形的周框矩形的左上角和右下角的座標。  
  
### <a name="return-value"></a>傳回值  
 如果作業成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 區域由結構或所指向的物件定義 `lpRect` 並儲存在 `CRgn` 物件。  
  
 區域的大小限制為 32767 的 32767 的邏輯單元或 64k 的記憶體，小者為準。  
  
 當它已完成使用區域，以建立 `CreateEllipticRgnIndirect` 函式，應用程式應該選取的裝置內容和使用的區域出 `DeleteObject` 函式，將它移除。  
  
### <a name="example"></a>範例  
  請參閱範例 [CRgn::CreateRectRgnIndirect](#crgn__createrectrgnindirect)。  
  
##  <a name="a-namecrgncreatefromdataa-crgncreatefromdata"></a><a name="crgn__createfromdata"></a>  CRgn::CreateFromData  
 從指定的區域和轉換資料，請建立區域。  
  
```  
BOOL CreateFromData(
    const XFORM* lpXForm,  
    int nCount,  
    const RGNDATA* pRgnData);
```  
  
### <a name="parameters"></a>參數  
 *lpXForm*  
 指向 [XFORM](../../mfc/reference/xform-structure.md) 資料結構，定義要在區域上執行的轉換。 如果這個指標是 **NULL**, ，會使用識別轉換。  
  
 `nCount`  
 指定所指向的位元組數目 `pRgnData`。  
  
 `pRgnData`  
 指向 [RGNDATA](../../mfc/reference/rgndata-structure.md) 包含區域資料的資料結構。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功則為非零，否則為 0。  
  
### <a name="remarks"></a>備註  
 應用程式可以擷取區域的資料，藉由呼叫 `CRgn::GetRegionData` 函式。  
  
##  <a name="a-namecrgncreatefrompatha-crgncreatefrompath"></a><a name="crgn__createfrompath"></a>  CRgn::CreateFromPath  
 從所選入指定的裝置內容的路徑建立區域。  
  
```  
BOOL CreateFromPath(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 識別包含封閉的路徑的裝置內容。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功則為非零，否則為 0。  
  
### <a name="remarks"></a>備註  
 裝置內容做為識別 `pDC` 參數必須包含已關閉的路徑。 之後 `CreateFromPath` 將轉換的路徑到區域時，Windows 會捨棄從裝置內容的封閉的路徑。  
  
##  <a name="a-namecrgncreatepolygonrgna-crgncreatepolygonrgn"></a><a name="crgn__createpolygonrgn"></a>  CRgn::CreatePolygonRgn  
 建立多邊形的區域。  
  
```  
BOOL CreatePolygonRgn(
    LPPOINT lpPoints,  
    int nCount,  
    int nMode);
```  
  
### <a name="parameters"></a>參數  
 `lpPoints`  
 指向陣列 **點** 結構或一組 `CPoint` 物件。 每個結構指定的 x 座標和 y 座標的一個多邊形頂點。  **點** 結構具有下列格式︰  
  
 `typedef struct tagPOINT {`  
  
 `int x;`  
  
 `int y;`  
  
 `} POINT;`  
  
 `nCount`  
 指定的數目 **點** 結構或 `CPoint` 陣列中的物件所指 `lpPoints`。  
  
 `nMode`  
 指定區域的填滿模式。 這個參數可以是 **替代** 或 **彎曲**。  
  
### <a name="return-value"></a>傳回值  
 如果作業成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 系統多邊形會自動關閉，必要時，所繪製一條線從最後一個頂點，第一個。 產生的區域會儲存在 `CRgn` 物件。  
  
 區域的大小限制為 32767 的 32767 的邏輯單元或 64k 的記憶體，小者為準。  
  
 多邊形填滿模式時 **替代**, ，系統會填滿上每個掃描線奇數和偶數多邊形側邊之間的區域。 也就是系統填滿區域的第一個和第二個端之間，第三個和第四個側邊之間等等。  
  
 多邊形填滿模式時 **彎曲**, ，系統會用來判斷是否要填滿的區域已繪製圖表的方向。 順時針或逆時針方向會繪製多邊形中的每個直線線段。 每當虛構的線圖外面括住的區域繪製出通過順時針直線線段，計數會漸增。 當行通過逆時針直線線段時，計數會遞減。 如果計數在線條數到達外的圖為非零，則會填滿區域。  
  
 應用程式已經完成時使用區域，以建立 `CreatePolygonRgn` 函式，它應該選取的裝置內容和使用的區域出 `DeleteObject` 函式，將它移除。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#146](../../mfc/codesnippet/CPP/crgn-class_3.cpp)]  
  
##  <a name="a-namecrgncreatepolypolygonrgna-crgncreatepolypolygonrgn"></a><a name="crgn__createpolypolygonrgn"></a>  CRgn::CreatePolyPolygonRgn  
 建立包含一系列的封閉的多邊形的區域。  
  
```  
BOOL CreatePolyPolygonRgn(
    LPPOINT lpPoints,  
    LPINT lpPolyCounts,  
    int nCount,  
    int nPolyFillMode);
```  
  
### <a name="parameters"></a>參數  
 `lpPoints`  
 指向陣列 **點** 結構或一組 `CPoint` 定義多邊形的頂點的物件。 每個多邊形必須明確地關閉，因為系統不會關閉它們自動。 多邊形會指定連續。  **點** 結構具有下列格式︰  
  
 `typedef struct tagPOINT {`  
  
 `int x;`  
  
 `int y;`  
  
 `} POINT;`  
  
 `lpPolyCounts`  
 整數的陣列指標。 第一個整數指定在中，第一個多邊形的頂點數目 `lpPoints` 第二個整數的陣列，指定的頂點數目在第二個多邊形，以此類推。  
  
 `nCount`  
 指定之整數的總數 `lpPolyCounts` 陣列。  
  
 `nPolyFillMode`  
 指定的多邊形填滿模式。 這個值可以是 **替代** 或 **彎曲**。  
  
### <a name="return-value"></a>傳回值  
 如果作業成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 產生的區域會儲存在 `CRgn` 物件。  
  
 多邊形可能不相鄰，或可能會重疊。  
  
 區域的大小限制為 32767 的 32767 的邏輯單元或 64k 的記憶體，小者為準。  
  
 多邊形填滿模式時 **替代**, ，系統會填滿上每個掃描線奇數和偶數多邊形側邊之間的區域。 也就是系統填滿區域的第一個和第二個端之間，第三個和第四個側邊之間等等。  
  
 多邊形填滿模式時 **彎曲**, ，系統會用來判斷是否要填滿的區域已繪製圖表的方向。 順時針或逆時針方向會繪製多邊形中的每個直線線段。 每當虛構的線圖外面括住的區域繪製出通過順時針直線線段，計數會漸增。 當行通過逆時針直線線段時，計數會遞減。 如果計數在線條數到達外的圖為非零，則會填滿區域。  
  
 應用程式已經完成時使用區域，以建立 `CreatePolyPolygonRgn` 函式，它應該選取的裝置內容和使用的區域出 [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#cgdiobject__deleteobject) 成員函式，將它移除。  
  
##  <a name="a-namecrgncreaterectrgna-crgncreaterectrgn"></a><a name="crgn__createrectrgn"></a>  CRgn::CreateRectRgn  
 建立矩形區域中所儲存 `CRgn` 物件。  
  
```  
BOOL CreateRectRgn(
    int x1,  
    int y1,  
    int x2,  
    int y2);
```  
  
### <a name="parameters"></a>參數  
 `x1`  
 指定區域的左上角的邏輯 x 座標。  
  
 `y1`  
 指定區域的左上角的邏輯 y 座標。  
  
 `x2`  
 指定邏輯區域右下角的 x 座標。  
  
 `y2`  
 指定邏輯區域右下角的 y 座標。  
  
### <a name="return-value"></a>傳回值  
 如果作業成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 區域的大小限制為 32767 的 32767 的邏輯單元或 64k 的記憶體，小者為準。  
  
 當它已完成使用所建立的區域 `CreateRectRgn`, ，應用程式應該使用 [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#cgdiobject__deleteobject) 成員函式來移除區域。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#147](../../mfc/codesnippet/CPP/crgn-class_4.cpp)]  
  
 如需其他範例，請參閱 [CRgn::CombineRgn](#crgn__combinergn)。  
  
##  <a name="a-namecrgncreaterectrgnindirecta-crgncreaterectrgnindirect"></a><a name="crgn__createrectrgnindirect"></a>  CRgn::CreateRectRgnIndirect  
 建立矩形區域中所儲存 `CRgn` 物件。  
  
```  
BOOL CreateRectRgnIndirect(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>參數  
 `lpRect`  
 指向 `RECT` 結構或 `CRect` 包含區域的左上角和右下角的邏輯座標的物件。  `RECT` 結構具有下列格式︰  
  
 `typedef struct tagRECT {`  
  
 `int left;`  
  
 `int top;`  
  
 `int right;`  
  
 `int bottom;`  
  
 `} RECT;`  
  
### <a name="return-value"></a>傳回值  
 如果作業成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 區域的大小限制為 32767 的 32767 的邏輯單元或 64k 的記憶體，小者為準。  
  
 當它已完成使用所建立的區域 `CreateRectRgnIndirect`, ，應用程式應該使用 [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#cgdiobject__deleteobject) 成員函式來移除區域。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#148](../../mfc/codesnippet/CPP/crgn-class_5.cpp)]  
  
##  <a name="a-namecrgncreateroundrectrgna-crgncreateroundrectrgn"></a><a name="crgn__createroundrectrgn"></a>  CRgn::CreateRoundRectRgn  
 建立具有圓角中所儲存的矩形區域 `CRgn` 物件。  
  
```  
BOOL CreateRoundRectRgn(
    int x1,  
    int y1,  
    int x2,  
    int y2,  
    int x3,  
    int y3);
```  
  
### <a name="parameters"></a>參數  
 `x1`  
 指定區域的左上角的邏輯 x 座標。  
  
 `y1`  
 指定區域的左上角的邏輯 y 座標。  
  
 `x2`  
 指定邏輯區域右下角的 x 座標。  
  
 `y2`  
 指定邏輯區域右下角的 y 座標。  
  
 *x3*  
 指定用來建立圓的角橢圓形的寬度。  
  
 `y3`  
 指定用來建立圓的角橢圓形的高度。  
  
### <a name="return-value"></a>傳回值  
 如果作業成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 區域的大小限制為 32767 的 32767 的邏輯單元或 64k 的記憶體，小者為準。  
  
 應用程式已經完成時使用區域，以建立 `CreateRoundRectRgn` 函式，它應該選取的裝置內容和使用的區域出 [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#cgdiobject__deleteobject) 成員函式，將它移除。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#149](../../mfc/codesnippet/CPP/crgn-class_6.cpp)]  
  
##  <a name="a-namecrgncrgna-crgncrgn"></a><a name="crgn__crgn"></a>  CRgn::CRgn  
 建構 `CRgn` 物件。  
  
```  
CRgn();
```  
  
### <a name="remarks"></a>備註  
  `m_hObject` 資料成員與一或多個其他物件初始化之前沒有包含有效的 Windows GDI 區域 `CRgn` 成員函式。  
  
### <a name="example"></a>範例  
  請參閱範例 [CRgn::CreateRoundRectRgn](#crgn__createroundrectrgn)。  
  
##  <a name="a-namecrgnequalrgna-crgnequalrgn"></a><a name="crgn__equalrgn"></a>  CRgn::EqualRgn  
 判斷指定的區域是否等於儲存在區域 `CRgn` 物件。  
  
```  
BOOL EqualRgn(CRgn* pRgn) const;

 
```  
  
### <a name="parameters"></a>參數  
 `pRgn`  
 識別之區域。  
  
### <a name="return-value"></a>傳回值  
 非零，如果兩個區域相等。否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#150](../../mfc/codesnippet/CPP/crgn-class_7.cpp)]  
  
##  <a name="a-namecrgnfromhandlea-crgnfromhandle"></a><a name="crgn__fromhandle"></a>  CRgn::FromHandle  
 若要將指標傳回 `CRgn` 物件控制代碼給 Windows 區域時。  
  
```  
static CRgn* PASCAL FromHandle(HRGN hRgn);
```  
  
### <a name="parameters"></a>參數  
 `hRgn`  
 指定 Windows 區域控制代碼。  
  
### <a name="return-value"></a>傳回值  
 指標 `CRgn` 物件。 如果函式不成功，傳回的值是 **NULL**。  
  
### <a name="remarks"></a>備註  
 如果 `CRgn` 物件尚未附加至控制代碼，暫存 `CRgn` 會建立並附加物件。 此暫存 `CRgn` 僅直到下一次應用程式在其事件迴圈中有閒置時間，在這次所有暫存圖形會刪除物件，物件才有效。 另一種說法是，此暫存物件的一個視窗訊息處理期間才有效。  
  
##  <a name="a-namecrgngetregiondataa-crgngetregiondata"></a><a name="crgn__getregiondata"></a>  CRgn::GetRegionData  
 描述區域資料中填入指定的緩衝區。  
  
```  
int GetRegionData(
    LPRGNDATA lpRgnData,  
    int nCount) const;

 
```  
  
### <a name="parameters"></a>參數  
 `lpRgnData`  
 指向 [RGNDATA](../../mfc/reference/rgndata-structure.md) 接收資訊的資料結構。 如果這個參數是 **NULL**, ，傳回的值包含所需的區域資料的位元組數目。  
  
 `nCount`  
 指定的大小，以位元組為單位， `lpRgnData` 緩衝區。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功和 `nCount` 指定足夠數量的位元組，傳回值永遠是 `nCount`。 如果函式失敗，或是 `nCount` 指定小於比足夠的位元組數目，則傳回值為 0 （錯誤）。  
  
### <a name="remarks"></a>備註  
 此資料包括組成區域的矩形維度。 此函式用於搭配 `CRgn::CreateFromData` 函式。  
  
##  <a name="a-namecrgngetrgnboxa-crgngetrgnbox"></a><a name="crgn__getrgnbox"></a>  CRgn::GetRgnBox  
 擷取週框的座標 `CRgn` 物件。  
  
```  
int GetRgnBox(LPRECT lpRect) const;

 
```  
  
### <a name="parameters"></a>參數  
 `lpRect`  
 指向 `RECT` 結構或 `CRect` 物件，以擷取週框的座標。  `RECT` 結構具有下列格式︰  
  
 `typedef struct tagRECT {`  
  
 `int left;`  
  
 `int top;`  
  
 `int right;`  
  
 `int bottom;`  
  
 `} RECT;`  
  
### <a name="return-value"></a>傳回值  
 指定的區域類型。 它可以是下列值之一︰  
  
- **COMPLEXREGION** 區域有重疊的框線。  
  
- **NULLREGION** 區域是空的。  
  
- **錯誤** `CRgn` 物件未指定有效的區域。  
  
- **SIMPLEREGION** 區域有沒有重疊的框線。  
  
### <a name="example"></a>範例  
  請參閱範例 [CRgn::CreatePolygonRgn](#crgn__createpolygonrgn)。  
  
##  <a name="a-namecrgnoffsetrgna-crgnoffsetrgn"></a><a name="crgn__offsetrgn"></a>  CRgn::OffsetRgn  
 將儲存在區域 `CRgn` 物件所指定的位移。  
  
```  
int OffsetRgn(
    int x,  
    int y);

 
int OffsetRgn(
    POINT point);
```  
  
### <a name="parameters"></a>參數  
 *x*  
 指定要向左移動，或向右的單位數目。  
  
 *y*  
 指定要上移或下移的單位數。  
  
 `point`  
 X 軸座標 `point` 指定要向左移動，或向右的單位數目。 Y 軸座標 `point` 指定要上移或下移的單位數。  `point` 參數可能 **點** 結構或 `CPoint` 物件。  
  
### <a name="return-value"></a>傳回值  
 新的區域類型。 它可以是下列值之一︰  
  
- **COMPLEXREGION** 區域有重疊的框線。  
  
- **錯誤** 區域控制代碼無效。  
  
- **NULLREGION** 區域是空的。  
  
- **SIMPLEREGION** 區域有沒有重疊的框線。  
  
### <a name="remarks"></a>備註  
 函式將移區域 *x* 沿著 x 軸單位並 *y* 沿著 y 軸的單位。  
  
 區域的座標值必須小於或等於 32767 而且大於或等於 – 32768。  *x* 和 *y* 參數必須小心選擇以防止無效的區域座標。  
  
### <a name="example"></a>範例  
  請參閱範例 [CRgn::CreateEllipticRgn](#crgn__createellipticrgn)。  
  
##  <a name="a-namecrgnoperatorhrgna-crgnoperator-hrgn"></a><a name="crgn__operator_hrgn"></a>  CRgn::operator HRGN  
 使用這個運算子來取得附加的 Windows GDI 控制代碼的 `CRgn` 物件。  
  
'' 運算子 HRGN() const;

 
```  
  
### Return Value  
 If successful, a handle to the Windows GDI object represented by the `CRgn` object; otherwise **NULL**.  
  
### Remarks  
 This operator is a casting operator, which supports direct use of an **HRGN** object.  
  
 For more information about using graphic objects, see the article [Graphic Objects](http://msdn.microsoft.com/library/windows/desktop/dd144962) in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="crgn__ptinregion"></a>  CRgn::PtInRegion  
 Checks whether the point given by *x* and *y* is in the region stored in the `CRgn` object.  
  
```  
BOOL PtInRegion (int x，  
    int y) const;

 
 
BOOL PtInRegion （點點） const;

 
```  
  
### Parameters  
 *x*  
 Specifies the logical x-coordinate of the point to test.  
  
 *y*  
 Specifies the logical y-coordinate of the point to test.  
  
 `point`  
 The x- and y-coordinates of `point` specify the x- and y-coordinates of the point to test the value of. The `point` parameter can either be a **POINT** structure or a `CPoint` object.  
  
### Return Value  
 Nonzero if the point is in the region; otherwise 0.  
  
##  <a name="crgn__rectinregion"></a>  CRgn::RectInRegion  
 Determines whether any part of the rectangle specified by `lpRect` is within the boundaries of the region stored in the `CRgn` object.  
  
```  
BOOL RectInRegion(LPCRECT lpRect) const;

 
```  
  
### Parameters  
 `lpRect`  
 Points to a `RECT` structure or `CRect` object. The `RECT` structure has the following form:  
  
 `typedef struct tagRECT {`  
  
 `int left;`  
  
 `int top;`  
  
 `int right;`  
  
 `int bottom;`  
  
 `} RECT;`  
  
### Return Value  
 Nonzero if any part of the specified rectangle lies within the boundaries of the region; otherwise 0.  
  
##  <a name="crgn__setrectrgn"></a>  CRgn::SetRectRgn  
 Creates a rectangular region.  
  
```  
void SetRectRgn (int x1，  
    int y1，  
    int x2，  
    int y2)。

 
void SetRectRgn (LPCRECT lpRect);
```  
  
### Parameters  
 `x1`  
 Specifies the x-coordinate of the upper-left corner of the rectangular region.  
  
 `y1`  
 Specifies the y-coordinate of the upper-left corner of the rectangular region.  
  
 `x2`  
 Specifies the x-coordinate of the lower-right corner of the rectangular region.  
  
 `y2`  
 Specifies the y-coordinate of the lower-right corner of the rectangular region.  
  
 `lpRect`  
 Specifies the rectangular region. Can be either a pointer to a `RECT` structure or a `CRect` object.  
  
### Remarks  
 Unlike [CreateRectRgn](#crgn__createrectrgn), however, it does not allocate any additional memory from the local Windows application heap. Instead, it uses the space allocated for the region stored in the `CRgn` object. This means that the `CRgn` object must already have been initialized with a valid Windows region before calling `SetRectRgn`. The points given by `x1`, `y1`, `x2`, and `y2` specify the minimum size of the allocated space.  
  
 Use this function instead of the `CreateRectRgn` member function to avoid calls to the local memory manager.  
  
## See Also  
 [CWnd Class](../../mfc/reference/cwnd-class.md)   
 [Hierarchy Chart](../../mfc/hierarchy-chart.md)




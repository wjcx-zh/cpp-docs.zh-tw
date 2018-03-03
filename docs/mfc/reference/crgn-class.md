---
title: "CRgn 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRgn
- AFXWIN/CRgn
- AFXWIN/CRgn::CRgn
- AFXWIN/CRgn::CombineRgn
- AFXWIN/CRgn::CopyRgn
- AFXWIN/CRgn::CreateEllipticRgn
- AFXWIN/CRgn::CreateEllipticRgnIndirect
- AFXWIN/CRgn::CreateFromData
- AFXWIN/CRgn::CreateFromPath
- AFXWIN/CRgn::CreatePolygonRgn
- AFXWIN/CRgn::CreatePolyPolygonRgn
- AFXWIN/CRgn::CreateRectRgn
- AFXWIN/CRgn::CreateRectRgnIndirect
- AFXWIN/CRgn::CreateRoundRectRgn
- AFXWIN/CRgn::EqualRgn
- AFXWIN/CRgn::FromHandle
- AFXWIN/CRgn::GetRegionData
- AFXWIN/CRgn::GetRgnBox
- AFXWIN/CRgn::OffsetRgn
- AFXWIN/CRgn::PtInRegion
- AFXWIN/CRgn::RectInRegion
- AFXWIN/CRgn::SetRectRgn
dev_langs:
- C++
helpviewer_keywords:
- CRgn [MFC], CRgn
- CRgn [MFC], CombineRgn
- CRgn [MFC], CopyRgn
- CRgn [MFC], CreateEllipticRgn
- CRgn [MFC], CreateEllipticRgnIndirect
- CRgn [MFC], CreateFromData
- CRgn [MFC], CreateFromPath
- CRgn [MFC], CreatePolygonRgn
- CRgn [MFC], CreatePolyPolygonRgn
- CRgn [MFC], CreateRectRgn
- CRgn [MFC], CreateRectRgnIndirect
- CRgn [MFC], CreateRoundRectRgn
- CRgn [MFC], EqualRgn
- CRgn [MFC], FromHandle
- CRgn [MFC], GetRegionData
- CRgn [MFC], GetRgnBox
- CRgn [MFC], OffsetRgn
- CRgn [MFC], PtInRegion
- CRgn [MFC], RectInRegion
- CRgn [MFC], SetRectRgn
ms.assetid: d904da84-76aa-481e-8780-b09485f49e64
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6d5556db19d7f0ec92f915dda49dfeb24390ab70
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="crgn-class"></a>CRgn 類別
封裝 Windows 繪圖裝置介面 (GDI) 區域。  
  
## <a name="syntax"></a>語法  
  
```  
class CRgn : public CGdiObject  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CRgn::CRgn](#crgn)|建構 `CRgn` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CRgn::CombineRgn](#combinergn)|設定`CRgn`物件，讓它相當於兩個指定的聯集`CRgn`物件。|  
|[CRgn::CopyRgn](#copyrgn)|設定`CRgn`物件，讓它是指定的複本`CRgn`物件。|  
|[CRgn::CreateEllipticRgn](#createellipticrgn)|初始化`CRgn`物件與橢圓形的區域。|  
|[CRgn::CreateEllipticRgnIndirect](#createellipticrgnindirect)|初始化`CRgn`物件所定義的橢圓形區域[RECT](../../mfc/reference/rect-structure1.md)結構。|  
|[CRgn::CreateFromData](#createfromdata)|從指定的地區和轉換資料，請建立區域。|  
|[CRgn::CreateFromPath](#createfrompath)|從選取至指定的裝置內容的路徑中建立區域。|  
|[CRgn::CreatePolygonRgn](#createpolygonrgn)|初始化`CRgn`物件與多邊形的區域。 系統多邊形會自動關閉，如有必要，藉由從最後一個頂點繪製一條線，第一個。|  
|[CRgn::CreatePolyPolygonRgn](#createpolypolygonrgn)|初始化`CRgn`物件與區域已關閉的多邊形的一系列所組成。 多邊形可能是脫離的或可能會重疊。|  
|[CRgn::CreateRectRgn](#createrectrgn)|初始化`CRgn`矩形區域的物件。|  
|[CRgn::CreateRectRgnIndirect](#createrectrgnindirect)|初始化`CRgn`物件所定義的矩形區域[RECT](../../mfc/reference/rect-structure1.md)結構。|  
|[CRgn::CreateRoundRectRgn](#createroundrectrgn)|初始化`CRgn`與具有圓角矩形區域的物件。|  
|[CRgn::EqualRgn](#equalrgn)|檢查兩個`CRgn`物件來判斷它們是否相等。|  
|[CRgn::FromHandle](#fromhandle)|將指標傳回至`CRgn`物件控制代碼提供 Windows 區域時。|  
|[CRgn::GetRegionData](#getregiondata)|描述給定的區域的資料填入指定的緩衝區。|  
|[CRgn::GetRgnBox](#getrgnbox)|擷取的週框的座標`CRgn`物件。|  
|[CRgn::OffsetRgn](#offsetrgn)|移動`CRgn`物件所指定的位移。|  
|[CRgn::PtInRegion](#ptinregion)|判斷指定的點是否在區域中。|  
|[CRgn::RectInRegion](#rectinregion)|判斷指定的任何的矩形部分是否為區域的界限內。|  
|[CRgn::SetRectRgn](#setrectrgn)|設定`CRgn`物件指定的矩形區域。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CRgn::operator HRGN](#operator_hrgn)|傳回包含在 Windows 控制代碼`CRgn`物件。|  
  
## <a name="remarks"></a>備註  
 區域是在視窗內的橢圓形或多邊形區域。 若要使用的區域，您可以使用類別的成員函式`CRgn`與裁剪函式定義為類別成員`CDC`。  
  
 成員函式`CRgn`建立、 改變和擷取其呼叫區域物件的相關資訊。  
  
 如需有關使用`CRgn`，請參閱[圖形物件](../../mfc/graphic-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CRgn`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="combinergn"></a>CRgn::CombineRgn  
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
 指定合併兩個來源區域時要執行的作業。 它可以是下列值之一：  
  
- **RGN_AND**使用重疊的區域，兩個區域 （交集）。  
  
- **RGN_COPY**建立一份區域 1 (由`pRgn1`)。  
  
- **RGN_DIFF**建立區域區 1 的區域所組成 (由`pRgn1`)，並不屬於區域 2 (由`pRgn2`)。  
  
- **RGN_OR**結合兩個區域中完整 （聯集）。  
  
- **RGN_XOR**結合兩個區域，但會移除重疊的區域。  
  
### <a name="return-value"></a>傳回值  
 指定產生的區域類型。 它可以是下列值之一：  
  
- **COMPLEXREGION**新區域具有重疊的框線。  
  
- **錯誤**建立任何新的區域。  
  
- **NULLREGION**新的區域是空的。  
  
- **SIMPLEREGION**新區域有任何重疊的框線。  
  
### <a name="remarks"></a>備註  
 區域的組合所指定`nCombineMode`。  
  
 兩個指定的區域組合，而產生的區域控制代碼會儲存在`CRgn`物件。 因此，任何區域儲存在`CRgn`結合區域所取代的物件。  
  
 區域的大小限制為 32767 的 32767 的邏輯單元或 64k 的記憶體，小者為準。  
  
 使用[CopyRgn](#copyrgn) ，只要將一個區域複製到另一個區域。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#144](../../mfc/codesnippet/cpp/crgn-class_1.cpp)]  
  
##  <a name="copyrgn"></a>CRgn::CopyRgn  
 複製所定義的區域`pRgnSrc`到`CRgn`物件。  
  
```  
int CopyRgn(CRgn* pRgnSrc);
```  
  
### <a name="parameters"></a>參數  
 `pRgnSrc`  
 識別現有的區域。  
  
### <a name="return-value"></a>傳回值  
 指定產生的區域類型。 它可以是下列值之一：  
  
- **COMPLEXREGION**新區域具有重疊的框線。  
  
- **錯誤**建立任何新的區域。  
  
- **NULLREGION**新的區域是空的。  
  
- **SIMPLEREGION**新區域有任何重疊的框線。  
  
### <a name="remarks"></a>備註  
 新的區域會取代先前儲存在區域`CRgn`物件。 此函式是特殊案例[CombineRgn](#combinergn)成員函式。  
  
### <a name="example"></a>範例  
  請參閱範例的[CRgn::CreateEllipticRgn](#createellipticrgn)。  
  
##  <a name="createellipticrgn"></a>CRgn::CreateEllipticRgn  
 建立橢圓形的區域。  
  
```  
BOOL CreateEllipticRgn(
    int x1,  
    int y1,  
    int x2,  
    int y2);
```  
  
### <a name="parameters"></a>參數  
 `x1`  
 指定邏輯橢圓形的周框左上角的 x 座標。  
  
 `y1`  
 指定邏輯橢圓形的周框左上角的 y 座標。  
  
 `x2`  
 指定邏輯橢圓形的周框矩形右下角的 x 座標。  
  
 `y2`  
 指定邏輯橢圓形的周框矩形右下角的 y 座標。  
  
### <a name="return-value"></a>傳回值  
 如果作業成功，則為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 區域由所指定的週框所定義`x1`， `y1`， `x2`，和`y2`。 區域儲存在`CRgn`物件。  
  
 區域的大小限制為 32767 的 32767 的邏輯單元或 64k 的記憶體，小者為準。  
  
 當它已完成使用區域，以建立`CreateEllipticRgn`函式，應用程式應該可以選取的裝置內容和使用的區域出`DeleteObject`函式，將它移除。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#145](../../mfc/codesnippet/cpp/crgn-class_2.cpp)]  
  
##  <a name="createellipticrgnindirect"></a>CRgn::CreateEllipticRgnIndirect  
 建立橢圓形的區域。  
  
```  
BOOL CreateEllipticRgnIndirect(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>參數  
 `lpRect`  
 指向`RECT`結構或`CRect`物件，其中包含邏輯橢圓形的周框左上角和右下角的座標。  
  
### <a name="return-value"></a>傳回值  
 如果作業成功，則為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 區域由所定義的結構或指向物件`lpRect`並儲存在`CRgn`物件。  
  
 區域的大小限制為 32767 的 32767 的邏輯單元或 64k 的記憶體，小者為準。  
  
 當它已完成使用區域，以建立`CreateEllipticRgnIndirect`函式，應用程式應該可以選取的裝置內容和使用的區域出`DeleteObject`函式，將它移除。  
  
### <a name="example"></a>範例  
  請參閱範例的[CRgn::CreateRectRgnIndirect](#createrectrgnindirect)。  
  
##  <a name="createfromdata"></a>CRgn::CreateFromData  
 從指定的地區和轉換資料，請建立區域。  
  
```  
BOOL CreateFromData(
    const XFORM* lpXForm,  
    int nCount,  
    const RGNDATA* pRgnData);
```  
  
### <a name="parameters"></a>參數  
 *lpXForm*  
 指向[XFORM](../../mfc/reference/xform-structure.md)定義區域上執行轉換的資料結構。 如果此指標為**NULL**，使用識別轉換。  
  
 `nCount`  
 指定所指向的位元組數目`pRgnData`。  
  
 `pRgnData`  
 指向[RGNDATA](../../mfc/reference/rgndata-structure.md)包含區域資料的資料結構。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功則為非零，否則為 0。  
  
### <a name="remarks"></a>備註  
 應用程式可以擷取區域的資料，藉由呼叫`CRgn::GetRegionData`函式。  
  
##  <a name="createfrompath"></a>CRgn::CreateFromPath  
 從選取至指定的裝置內容的路徑中建立區域。  
  
```  
BOOL CreateFromPath(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 識別裝置內容，其中包含已關閉的路徑。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功則為非零，否則為 0。  
  
### <a name="remarks"></a>備註  
 所識別的裝置內容`pDC`參數必須包含已關閉的路徑。 之後`CreateFromPath`路徑到區域時，Windows 將會捨棄從裝置內容已關閉的路徑。  
  
##  <a name="createpolygonrgn"></a>CRgn::CreatePolygonRgn  
 建立多邊形的區域。  
  
```  
BOOL CreatePolygonRgn(
    LPPOINT lpPoints,  
    int nCount,  
    int nMode);
```  
  
### <a name="parameters"></a>參數  
 `lpPoints`  
 指向陣列**點**結構或陣列`CPoint`物件。 每個結構指定的 x 座標和 y 座標一個多邊形頂點。 **點**結構具有下列格式：  
  
 `typedef struct tagPOINT {`  
  
 `int x;`  
  
 `int y;`  
  
 `} POINT;`  
  
 `nCount`  
 指定的數目**點**結構或`CPoint`所指陣列中的物件`lpPoints`。  
  
 `nMode`  
 指定區域的填滿模式。 這個參數可以是**替代**或**捲繞**。  
  
### <a name="return-value"></a>傳回值  
 如果作業成功，則為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 系統多邊形會自動關閉，如有必要，藉由從最後一個頂點繪製一條線，第一個。 產生的區域會儲存在`CRgn`物件。  
  
 區域的大小限制為 32767 的 32767 的邏輯單元或 64k 的記憶體，小者為準。  
  
 多邊形填滿模式時**替代**，系統會掃描一行奇數和偶數多邊形側邊之間的區域填滿。 也就是說，系統會填滿區域之間的第一個和第二個邊，等第三個和第四個側邊之間。  
  
 多邊形填滿模式時**捲繞**，系統會用來判斷是否要填滿區域已繪製圖形的方向。 順時針或逆時針方向會繪製多邊形中的每個直線線段。 每當取自括住的區域圖外面虛數行通過順時針旋轉的直線線段的計數會遞增。 當行通過逆時針算起的直線線段時，計數會遞減。 如果行達到圖的外面時計數則為非零，則會填滿區域。  
  
 應用程式已經完成時使用區域，以建立`CreatePolygonRgn`函式，它應該選取的裝置內容和使用的區域出`DeleteObject`函式，將它移除。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#146](../../mfc/codesnippet/cpp/crgn-class_3.cpp)]  
  
##  <a name="createpolypolygonrgn"></a>CRgn::CreatePolyPolygonRgn  
 建立區域，已關閉的多邊形的一系列所組成。  
  
```  
BOOL CreatePolyPolygonRgn(
    LPPOINT lpPoints,  
    LPINT lpPolyCounts,  
    int nCount,  
    int nPolyFillMode);
```  
  
### <a name="parameters"></a>參數  
 `lpPoints`  
 指向陣列**點**結構或陣列`CPoint`定義的多邊形頂點的物件。 每個多邊形必須明確地關閉，因為系統不會關閉它們自動。 多邊形會指定連續。 **點**結構具有下列格式：  
  
 `typedef struct tagPOINT {`  
  
 `int x;`  
  
 `int y;`  
  
 `} POINT;`  
  
 `lpPolyCounts`  
 指向陣列的整數。 第一個整數指定在中，第一個多邊形的頂點數目`lpPoints`第二個整數的陣列，指定第二個多邊形、 等等的頂點數目。  
  
 `nCount`  
 指定之整數的總數`lpPolyCounts`陣列。  
  
 `nPolyFillMode`  
 指定的多邊形填滿模式。 這個值可以是**替代**或**捲繞**。  
  
### <a name="return-value"></a>傳回值  
 如果作業成功，則為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 產生的區域會儲存在`CRgn`物件。  
  
 多邊形可能是脫離的或可能會重疊。  
  
 區域的大小限制為 32767 的 32767 的邏輯單元或 64k 的記憶體，小者為準。  
  
 多邊形填滿模式時**替代**，系統會掃描一行奇數和偶數多邊形側邊之間的區域填滿。 也就是說，系統會填滿區域之間的第一個和第二個邊，等第三個和第四個側邊之間。  
  
 多邊形填滿模式時**捲繞**，系統會用來判斷是否要填滿區域已繪製圖形的方向。 順時針或逆時針方向會繪製多邊形中的每個直線線段。 每當取自括住的區域圖外面虛數行通過順時針旋轉的直線線段的計數會遞增。 當行通過逆時針算起的直線線段時，計數會遞減。 如果行達到圖的外面時計數則為非零，則會填滿區域。  
  
 應用程式已經完成時使用區域，以建立`CreatePolyPolygonRgn`函式，它應該選取的裝置內容和使用的區域出[CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject)成員函式，將它移除。  
  
##  <a name="createrectrgn"></a>CRgn::CreateRectRgn  
 建立矩形區域中所儲存`CRgn`物件。  
  
```  
BOOL CreateRectRgn(
    int x1,  
    int y1,  
    int x2,  
    int y2);
```  
  
### <a name="parameters"></a>參數  
 `x1`  
 指定邏輯區的左上角的 x 座標。  
  
 `y1`  
 指定邏輯區的左上角的 y 座標。  
  
 `x2`  
 指定邏輯區域右下角的 x 座標。  
  
 `y2`  
 指定邏輯區域右下角的 y 座標。  
  
### <a name="return-value"></a>傳回值  
 如果作業成功，則為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 區域的大小限制為 32767 的 32767 的邏輯單元或 64k 的記憶體，小者為準。  
  
 當它已完成使用所建立的區域`CreateRectRgn`，應用程式應該使用[CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject)成員函式來移除區域。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#147](../../mfc/codesnippet/cpp/crgn-class_4.cpp)]  
  
 如需其他範例，請參閱[CRgn::CombineRgn](#combinergn)。  
  
##  <a name="createrectrgnindirect"></a>CRgn::CreateRectRgnIndirect  
 建立矩形區域中所儲存`CRgn`物件。  
  
```  
BOOL CreateRectRgnIndirect(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>參數  
 `lpRect`  
 指向`RECT`結構或`CRect`含有區域的左上角和右下角的邏輯座標的物件。 `RECT`結構具有下列格式：  
  
 `typedef struct tagRECT {`  
  
 `int left;`  
  
 `int top;`  
  
 `int right;`  
  
 `int bottom;`  
  
 `} RECT;`  
  
### <a name="return-value"></a>傳回值  
 如果作業成功，則為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 區域的大小限制為 32767 的 32767 的邏輯單元或 64k 的記憶體，小者為準。  
  
 當它已完成使用所建立的區域`CreateRectRgnIndirect`，應用程式應該使用[CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject)成員函式來移除區域。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#148](../../mfc/codesnippet/cpp/crgn-class_5.cpp)]  
  
##  <a name="createroundrectrgn"></a>CRgn::CreateRoundRectRgn  
 建立具有圓角中所儲存的矩形區域`CRgn`物件。  
  
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
 指定邏輯區的左上角的 x 座標。  
  
 `y1`  
 指定邏輯區的左上角的 y 座標。  
  
 `x2`  
 指定邏輯區域右下角的 x 座標。  
  
 `y2`  
 指定邏輯區域右下角的 y 座標。  
  
 *x3*  
 指定用來建立圓的角的省略符號的寬度。  
  
 `y3`  
 指定用來建立圓的角的省略符號的高度。  
  
### <a name="return-value"></a>傳回值  
 如果作業成功，則為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 區域的大小限制為 32767 的 32767 的邏輯單元或 64k 的記憶體，小者為準。  
  
 應用程式已經完成時使用區域，以建立`CreateRoundRectRgn`函式，它應該選取的裝置內容和使用的區域出[CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject)成員函式，將它移除。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#149](../../mfc/codesnippet/cpp/crgn-class_6.cpp)]  
  
##  <a name="crgn"></a>CRgn::CRgn  
 建構 `CRgn` 物件。  
  
```  
CRgn();
```  
  
### <a name="remarks"></a>備註  
 `m_hObject`直到一或多個其他物件初始化資料成員不包含有效的 Windows GDI 區域`CRgn`成員函式。  
  
### <a name="example"></a>範例  
  請參閱範例的[CRgn::CreateRoundRectRgn](#createroundrectrgn)。  
  
##  <a name="equalrgn"></a>CRgn::EqualRgn  
 判斷是否等於儲存在地區指定的地區`CRgn`物件。  
  
```  
BOOL EqualRgn(CRgn* pRgn) const;  
```  
  
### <a name="parameters"></a>參數  
 `pRgn`  
 識別的區域。  
  
### <a name="return-value"></a>傳回值  
 如果兩個區域相等則為非零否則便是 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#150](../../mfc/codesnippet/cpp/crgn-class_7.cpp)]  
  
##  <a name="fromhandle"></a>CRgn::FromHandle  
 將指標傳回至`CRgn`物件控制代碼提供 Windows 區域時。  
  
```  
static CRgn* PASCAL FromHandle(HRGN hRgn);
```  
  
### <a name="parameters"></a>參數  
 `hRgn`  
 指定 Windows 區域控制代碼。  
  
### <a name="return-value"></a>傳回值  
 指標`CRgn`物件。 如果函式不成功，傳回值是**NULL**。  
  
### <a name="remarks"></a>備註  
 如果`CRgn`物件未附加至控制代碼，暫存`CRgn`物件會建立並附加。 此暫存`CRgn`僅直到下一次應用程式有其事件迴圈中的閒置時間，在這次所有暫存圖形已刪除物件，物件才有效。 另一種說法是，暫存物件的一個視窗訊息處理期間才有效。  
  
##  <a name="getregiondata"></a>CRgn::GetRegionData  
 描述區域的資料填入指定的緩衝區。  
  
```  
int GetRegionData(
    LPRGNDATA lpRgnData,  
    int nCount) const;  
```  
  
### <a name="parameters"></a>參數  
 `lpRgnData`  
 指向[RGNDATA](../../mfc/reference/rgndata-structure.md)接收資訊的資料結構。 如果這個參數是**NULL**，傳回的值包含所需的區域資料的位元組數目。  
  
 `nCount`  
 指定的大小，以位元組為單位，`lpRgnData`緩衝區。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功和`nCount`指定足夠數量的位元組，則傳回值一律是`nCount`。 如果函式失敗，或者如果`nCount`指定小於比足夠的位元組數目，則傳回值是 0 （錯誤）。  
  
### <a name="remarks"></a>備註  
 此資料包含組成區域的矩形的維度。 此函式用於搭配`CRgn::CreateFromData`函式。  
  
##  <a name="getrgnbox"></a>CRgn::GetRgnBox  
 擷取的週框的座標`CRgn`物件。  
  
```  
int GetRgnBox(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>參數  
 `lpRect`  
 指向`RECT`結構或`CRect`物件，以擷取週框的座標。 `RECT`結構具有下列格式：  
  
 `typedef struct tagRECT {`  
  
 `int left;`  
  
 `int top;`  
  
 `int right;`  
  
 `int bottom;`  
  
 `} RECT;`  
  
### <a name="return-value"></a>傳回值  
 指定區域的類型。 它可以是下列值之一：  
  
- **COMPLEXREGION**區域具有重疊的框線。  
  
- **NULLREGION**區域是空的。  
  
- **錯誤**`CRgn`物件未指定有效的區域。  
  
- **SIMPLEREGION**區域有任何重疊的框線。  
  
### <a name="example"></a>範例  
  請參閱範例的[CRgn::CreatePolygonRgn](#createpolygonrgn)。  
  
##  <a name="offsetrgn"></a>CRgn::OffsetRgn  
 將儲存在區域`CRgn`物件所指定的位移。  
  
```  
int OffsetRgn(
    int x,  
    int y);  
  
int OffsetRgn(POINT point);
```  
  
### <a name="parameters"></a>參數  
 *x*  
 指定要向左移動或向右的單位數目。  
  
 *y*  
 指定要上移或下移的單位數。  
  
 `point`  
 X 軸座標`point`指定要向左移動或向右的單位數目。 Y 座標`point`指定要上移或下移的單位數。 `point`參數可以是**點**結構或`CPoint`物件。  
  
### <a name="return-value"></a>傳回值  
 新的區域類型。 它可以是下列值之一：  
  
- **COMPLEXREGION**區域具有重疊的框線。  
  
- **錯誤**區域控制代碼無效。  
  
- **NULLREGION**區域是空的。  
  
- **SIMPLEREGION**區域有任何重疊的框線。  
  
### <a name="remarks"></a>備註  
 此函式移動區域*x*沿著 x 軸單位並*y*沿著 y 軸的單位。  
  
 區域的座標值必須小於或等於 32,767 且大於或等於-32768。 *x*和*y*參數必須小心選擇以防止無效的區域座標。  
  
### <a name="example"></a>範例  
  請參閱範例的[CRgn::CreateEllipticRgn](#createellipticrgn)。  
  
##  <a name="operator_hrgn"></a>CRgn::operator HRGN  
 使用此運算子，以取得附加的 Windows GDI 控制代碼的`CRgn`物件。  
  
```  
operator HRGN() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果成功，Windows GDI 物件的控制代碼來表示`CRgn`物件; 否則**NULL**。  
  
### <a name="remarks"></a>備註  
 這位操作員便轉型運算子，可支援直接使用**HRGN**物件。  
  
 如需使用 圖形物件的詳細資訊，請參閱文章[圖形物件](http://msdn.microsoft.com/library/windows/desktop/dd144962)Windows SDK 中。  
  
##  <a name="ptinregion"></a>CRgn::PtInRegion  
 檢查是否以指定的點*x*和*y*儲存在區域中`CRgn`物件。  
  
```  
BOOL PtInRegion(
    int x,  
    int y) const;  
  
BOOL PtInRegion(POINT point) const;  
```  
  
### <a name="parameters"></a>參數  
 *x*  
 指定要測試的點的邏輯 x 座標。  
  
 *y*  
 指定要測試的點的邏輯 y 座標。  
  
 `point`  
 X 和 y 座標的`point`指定要測試的值的點 x 和 y 座標。 `point`參數可以是**點**結構或`CPoint`物件。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果點區域。否則便是 0。  
  
##  <a name="rectinregion"></a>CRgn::RectInRegion  
 判斷指定的矩形的任何部分`lpRect`是儲存在區域的界限內`CRgn`物件。  
  
```  
BOOL RectInRegion(LPCRECT lpRect) const;  
```  
  
### <a name="parameters"></a>參數  
 `lpRect`  
 指向`RECT`結構或`CRect`物件。 `RECT`結構具有下列格式：  
  
 `typedef struct tagRECT {`  
  
 `int left;`  
  
 `int top;`  
  
 `int right;`  
  
 `int bottom;`  
  
 `} RECT;`  
  
### <a name="return-value"></a>傳回值  
 為非零，如果指定的任何的矩形部分位於界限內的區域。否則便是 0。  
  
##  <a name="setrectrgn"></a>CRgn::SetRectRgn  
 建立矩形區域。  
  
```  
void SetRectRgn(
    int x1,  
    int y1,  
    int x2,  
    int y2);  
  
void SetRectRgn(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>參數  
 `x1`  
 指定的矩形區域的左上角的 x 座標。  
  
 `y1`  
 指定的矩形區域的左上角的 y 座標。  
  
 `x2`  
 指定的矩形區域的右下角的 x 座標。  
  
 `y2`  
 指定的矩形區域的右下角的 y 座標。  
  
 `lpRect`  
 指定的矩形區域。 可以是以指標`RECT`結構或`CRect`物件。  
  
### <a name="remarks"></a>備註  
 不同於[CreateRectRgn](#createrectrgn)，不過，它不會配置任何額外記憶體從本機 Windows 應用程式堆積。 相反地，它會使用區域儲存在所配置的空間`CRgn`物件。 這表示`CRgn`物件必須具有已經初始化與有效的 Windows 地區，然後再呼叫`SetRectRgn`。 所指定的點`x1`， `y1`， `x2`，和`y2`指定的已配置空間的最小大小。  
  
 使用此函式，而不是`CreateRectRgn`成員函式，以避免呼叫本機記憶體管理員。  
  
## <a name="see-also"></a>請參閱  
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)




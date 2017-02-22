---
title: "CRect 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CRect"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LPCRECT 資料類型"
  - "CRect 類別"
  - "LPRECT 運算子"
  - "RECT 結構"
ms.assetid: dee4e752-15d6-4db4-b68f-1ad65b2ed6ca
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CRect 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

類似於 Windows [RECT](../../mfc/reference/rect-structure1.md) 結構。  
  
## <a name="syntax"></a>語法  
  
```  
class CRect : public tagRECT  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CRect::CRect](#crect__crect)|建構 `CRect` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CRect::BottomRight](#crect__bottomright)|傳回的右下角點 `CRect`。|  
|[CRect::CenterPoint](#crect__centerpoint)|傳回的中心點 `CRect`。|  
|[CRect::CopyRect](#crect__copyrect)|將複製的來源矩形的尺寸 `CRect`。|  
|[CRect::DeflateRect](#crect__deflaterect)|減少的高度與寬度 `CRect`。|  
|[CRect::EqualRect](#crect__equalrect)|決定是否 `CRect` 是否等於指定的矩形。|  
|[CRect::Height](#crect__height)|計算的高度 `CRect`。|  
|[CRect::InflateRect](#crect__inflaterect)|增加的高度與寬度 `CRect`。|  
|[CRect::IntersectRect](#crect__intersectrect)|設定 `CRect` 等於兩個矩形的交集。|  
|[CRect::IsRectEmpty](#crect__isrectempty)|決定是否 `CRect` 是空的。 `CRect` 如果，是空的寬度或高度為 0。|  
|[CRect::IsRectNull](#crect__isrectnull)|決定是否 **頂端**, ，**下**, ，**左**, ，和 **右** 成員變數是所有等於 0。|  
|[CRect::MoveToX](#crect__movetox)|移動 `CRect` 到指定的 x 座標。|  
|[CRect::MoveToXY](#crect__movetoxy)|移動 `CRect` 來指定 x 和 y 座標。|  
|[CRect::MoveToY](#crect__movetoy)|移動 `CRect` 到指定的 y 座標。|  
|[Normalizerect](#crect__normalizerect)|標準化的高度和寬度 `CRect`。|  
|[CRect::OffsetRect](#crect__offsetrect)|移動 `CRect` 所指定的位移。|  
|[CRect::PtInRect](#crect__ptinrect)|判斷指定的點是否位於內 `CRect`。|  
|[CRect::SetRect](#crect__setrect)|設定維度的 `CRect`。|  
|[CRect::SetRectEmpty](#crect__setrectempty)|設定 `CRect` 來為空的矩形 （所有座標都等於 0）。|  
|[CRect::Size](#crect__size)|計算的大小 `CRect`。|  
|[CRect::SubtractRect](#crect__subtractrect)|減去另一個矩形。|  
|[CRect::TopLeft](#crect__topleft)|傳回的左上角點 `CRect`。|  
|[CRect::UnionRect](#crect__unionrect)|設定 `CRect` 等於兩個矩形的聯集。|  
|[CRect::Width](#crect__width)|計算的寬度 `CRect`。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CRect::operator-](#crect__operator_-)|減去指定的位移，從 `CRect` 或 deflate `CRect` ，並傳回所產生的 `CRect`。|  
|[CRect::operator LPCRECT](#crect__operator_lpcrect)|將轉換 `CRect` 至 **LPCRECT**。|  
|[CRect::operator LPRECT](#crect__operator_lprect)|將轉換 `CRect` 到 `LPRECT`。|  
|[CRect::operator ！ =](#crect__operator__neq)|決定是否 `CRect` 不等於矩形。|  
|[CRect::operator &amp;](#crect__operator__amp_)|建立交集 `CRect` 和矩形，並傳回所產生的 `CRect`。|  
|[CRect::operator &amp;=](#crect__operator__amp__eq)|設定 `CRect` 等於交集 `CRect` 和矩形。|  
|[CRect::operator |](#crect__operator__or)|建立的聯集 `CRect` 和矩形，並傳回所產生的 `CRect`。|  
|[CRect::operator |=](#crect__operator__or_eq)|設定 `CRect` 等於的聯集 `CRect` 和矩形。|  
|[CRect::operator +](#crect__operator__add)|將指定的位移 `CRect` 或擴大 `CRect` ，並傳回所產生的 `CRect`。|  
|[CRect::operator + =](#crect__operator__add_eq)|加入至指定的位移 `CRect` 或擴大 `CRect`。|  
|[CRect::operator =](#crect__operator__eq)|將複製的矩形維度 `CRect`。|  
|[CRect::operator =](#crect__operator_-_eq)|減去指定的位移，從 `CRect` 或 deflate `CRect`。|  
|[CRect::operator = =](#crect__operator__eq_eq)|決定是否 `CRect` 等於矩形。|  
  
## <a name="remarks"></a>備註  
 `CRect` 也包含成員函式來管理 `CRect` 物件和 Windows `RECT` 結構。  
  
 A `CRect` 物件可以傳遞做為函式參數每當 `RECT` 結構 **LPCRECT**, ，或 `LPRECT` 可以傳遞。  
  
> [!NOTE]
>  這個類別衍生自 **tagRECT** 結構。 (名稱 **tagRECT** 是小於-常用名稱 `RECT` 結構。)這表示，資料成員 ( **左**, ，**頂端**, ，**右**, ，和 **下**) 的 `RECT` 結構是可存取的資料成員的 `CRect`。  
  
 A `CRect` 包含成員變數來定義矩形的左上角和右下角的點。  
  
 當指定 `CRect`, ，您必須非常小心建構它，都會被標準化 — 換句話說，這類的左方座標值是否小於右邊和 top 會小於底部。 比方說，左上角 (10,10) 和右下方 (20,20) 定義的標準化的矩形左上角 (20,20) 但右下方 (10,10) 定義非標準化的矩形。 如果矩形不會正規化，許多 `CRect` 成員函式可能會傳回不正確的結果。 (請參閱 [Normalizerect](#crect__normalizerect) 如需這些函式的清單。)在呼叫的函式需要標準化的矩形之前，您可以將非標準化矩形正規化藉由呼叫 `NormalizeRect` 函式。  
  
 操作時請小心 `CRect` 與 [CDC::DPtoLP] (.../Topic/CDC%20Class.md#cdc__dptolp 和 [CDC::LPtoDP] (.../Topic/CDC%20Class.md#cdc__lptodp 成員函式。 顯示內容的對應模式，如果會 y 範圍中為負數，做為 `MM_LOENGLISH`, ，然後 `CDC::DPtoLP` 會將轉換 `CRect` 使其 top 大於底部。 這類函數 **高度** 和 **大小** 會傳回已轉換的高度的負數值 `CRect`, ，矩形會非正規化。  
  
 當使用多載 `CRect` 運算子，在第一個運算元必須是 `CRect`; 第二個可以 [RECT](../../mfc/reference/rect-structure1.md) 結構或 `CRect` 物件。  
  
> [!NOTE]
>  如需有關共用公用程式類別 (例如 `CRect`)，請參閱 [共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `tagRECT`  
  
 `CRect`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atltypes.h  
  
##  <a name="a-namecrectbottomrighta-crectbottomright"></a><a name="crect__bottomright"></a>  CRect::BottomRight  
 做為參考傳回座標 [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) 物件中包含的 `CRect`。  
  
```  
 
CPoint& BottomRight() throw();

const CPoint& BottomRight() const throw();

 
```  
  
### <a name="return-value"></a>傳回值  
 矩形的右下角的座標。  
  
### <a name="remarks"></a>備註  
 您可以使用此函式，取得或設定矩形的右下角。 指派運算子左邊使用此函式，以設定邊角。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#35](../../atl-mfc-shared/codesnippet/CPP/crect-class_1.cpp)]  
  
##  <a name="a-namecrectcenterpointa-crectcenterpoint"></a><a name="crect__centerpoint"></a>  CRect::CenterPoint  
 計算的中心點 `CRect` 藉由加入左和右值並除以二，和新增的上方和下方的值除以兩個。  
  
```  
CPoint CenterPoint() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 A `CPoint` 物件的中心點 `CRect`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#36](../../atl-mfc-shared/codesnippet/CPP/crect-class_2.cpp)]  
  
##  <a name="a-namecrectcopyrecta-crectcopyrect"></a><a name="crect__copyrect"></a>  CRect::CopyRect  
 複製 `lpSrcRect` 到矩形 `CRect`。  
  
```  
 
void CopyRect(
LPCRECT   
lpSrcRect) throw();

 
```  
  
### <a name="parameters"></a>參數  
 `lpSrcRect`  
 指向 [RECT](../../mfc/reference/rect-structure1.md) 結構或 `CRect` 要複製的物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#37](../../atl-mfc-shared/codesnippet/CPP/crect-class_3.cpp)]  
  
##  <a name="a-namecrectcrecta-crectcrect"></a><a name="crect__crect"></a>  CRect::CRect  
 建構 `CRect` 物件。  
  
```  
 
    CRect() throw();
CRect(
 int    
    l ,  
    int 
    t ,  
    int 
    r ,  
    int 
    b) throw();
CRect(
 const RECT& 
    srcRect) throw();
CRect(
 LPCRECT    
    lpSrcRect) throw();
CRect(
 POINT    
    point ,  
    SIZE 
    size) throw();
CRect(
 POINT    
    topLeft ,  
    POINT 
    bottomRight) throw();

 
```  
  
### <a name="parameters"></a>參數  
 *l*  
 指定的左方的位置 `CRect`。  
  
 *t*  
 指定頂端 `CRect`。  
  
 *r*  
 指定正確的位置 `CRect`。  
  
 *b*  
 指定底部 `CRect`。  
  
 *srcRect*  
 是指 [RECT](../../mfc/reference/rect-structure1.md) 結構的座標 `CRect`。  
  
 `lpSrcRect`  
 指向 `RECT` 結構的座標 `CRect`。  
  
 `point`  
 指定要建構的矩形的原點。 對應至左上角。  
  
 `size`  
 會指定從左上角到右下角的矩形來建構。  
  
 *topLeft*  
 指定的左上角位置 `CRect`。  
  
 *bottomRight*  
 指定的右下角位置 `CRect`。  
  
### <a name="remarks"></a>備註  
 如果任何引數不指定 **左**, ，**頂端**, ，**右**, ，和 **下** 成員不會初始化。  
  
  `CRect`( **Const RECT &**) 和 `CRect`( **LPCRECT**) 建構函式執行 [CopyRect](#crect__copyrect)。 其他建構函式直接初始化物件的成員變數。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#38](../../atl-mfc-shared/codesnippet/CPP/crect-class_4.cpp)]  
  
##  <a name="a-namecrectdeflaterecta-crectdeflaterect"></a><a name="crect__deflaterect"></a>  CRect::DeflateRect  
 `DeflateRect` 「 洩氣 」 `CRect` 其邊邁向置。  
  
```  
 
    void DeflateRect(
    int 
    x ,  
    int 
    y) throw();
void DeflateRect(
    SIZE 
    size) throw();
void DeflateRect(
    LPCRECT 
    lpRect) throw();
void DeflateRect(
    int 
    l ,  
    int 
    t ,  
    int 
    r ,  
    int 
    b) throw();

 
```  
  
### <a name="parameters"></a>參數  
 *x*  
 指定要 deflate 左邊的單位數和右邊 `CRect`。  
  
 *y*  
 指定要 deflate 頂端和底部的單位數 `CRect`。  
  
 `size`  
 A [大小](http://msdn.microsoft.com/library/windows/desktop/dd145106) 或 [CSize](../../atl-mfc-shared/reference/csize-class.md) ，指定要 deflate 的單位數 `CRect`。  `cx` 值會指定要 deflate 左邊和右邊的單位數和 `cy` 值會指定要 deflate 頂端和底端的單位數。  
  
 `lpRect`  
 指向 [RECT](../../mfc/reference/rect-structure1.md) 結構或 `CRect` ，指定要 deflate 每一端的單位數。  
  
 *l*  
 指定要 deflate 左下的方的單位數 `CRect`。  
  
 *t*  
 指定要 deflate 頂端的單位數 `CRect`。  
  
 *r*  
 指定要 deflate 右側的單位數 `CRect`。  
  
 *b*  
 指定要 deflate 底部的單位數 `CRect`。  
  
### <a name="remarks"></a>備註  
 若要這樣做， `DeflateRect` 加入 left 和 top 的單位，並且減去從右側和底端的單位。 參數的 `DeflateRect` 簽署值; 正值 deflate `CRect` 和負值水平地擴大它。  
  
 前兩個多載 deflate 配對的另一邊的 `CRect` 使其總寬度會減少兩次 *x* (或 `cx`) 和總高度就會減少兩次 *y* (或 `cy`)。 其他兩個多載 deflate 每一面 `CRect` 各自。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#39](../../atl-mfc-shared/codesnippet/CPP/crect-class_5.cpp)]  
  
##  <a name="a-namecrectequalrecta-crectequalrect"></a><a name="crect__equalrect"></a>  CRect::EqualRect  
 決定是否 `CRect` 是否等於指定的矩形。  
  
```  
 
BOOL EqualRect(
LPCRECT   
lpRect) const throw();

 
```  
  
### <a name="parameters"></a>參數  
 `lpRect`  
 指向 [RECT](../../mfc/reference/rect-structure1.md) 結構或 `CRect` 物件，其中包含矩形的左上角和右下角座標。  
  
### <a name="return-value"></a>傳回值  
 非零，如果兩個矩形有相同的最上方、 左側、 底端和正確的值;否則為 0。  
  
> [!NOTE]
>  這兩個矩形必須正規化，或此函式可能會失敗。 您可以呼叫 [NormalizeRect](#crect__normalizerect) 正規化之前呼叫這個函式的矩形。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#40](../../atl-mfc-shared/codesnippet/CPP/crect-class_6.cpp)]  
  
##  <a name="a-namecrectheighta-crectheight"></a><a name="crect__height"></a>  CRect::Height  
 計算的高度 `CRect` 減去從底部值最高的值。  
  
```  
int Height() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 高度 `CRect`。  
  
### <a name="remarks"></a>備註  
 產生的值可以是負數。  
  
> [!NOTE]
>  矩形必須正規化，或此函式可能會失敗。 您可以呼叫 [NormalizeRect](#crect__normalizerect) 正規化之前呼叫這個函式的矩形。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#41](../../atl-mfc-shared/codesnippet/CPP/crect-class_7.cpp)]  
  
##  <a name="a-namecrectinflaterecta-crectinflaterect"></a><a name="crect__inflaterect"></a>  CRect::InflateRect  
 `InflateRect` 擴大 `CRect` 遠離其中心移動其側邊。  
  
```  
 
    void InflateRect(
    int 
    x ,  
    int 
    y) throw();
void InflateRect(
    SIZE 
    size) throw();
void InflateRect(
    LPCRECT 
    lpRect) throw();
void InflateRect(
    int 
    l ,  
    int 
    t ,  
    int 
    r ,  
    int 
    b) throw();

 
```  
  
### <a name="parameters"></a>參數  
 *x*  
 指定要水平地擴大左邊的單位數和右邊 `CRect`。  
  
 *y*  
 指定要水平地擴大頂端和底部的單位數 `CRect`。  
  
 `size`  
 A [大小](http://msdn.microsoft.com/library/windows/desktop/dd145106) 或 [CSize](../../atl-mfc-shared/reference/csize-class.md) ，指定要水平地擴大的單位數 `CRect`。  `cx` 值會指定要水平地擴大左邊和右邊的單位數和 `cy` 值會指定要水平地擴大的頂端和底部的單位數。  
  
 `lpRect`  
 指向 [RECT](../../mfc/reference/rect-structure1.md) 結構或 `CRect` ，指定要水平地擴大每一端的單位數。  
  
 *l*  
 指定要水平地擴大左下的方的單位數 `CRect`。  
  
 *t*  
 指定要水平地擴大頂端的單位數 `CRect`。  
  
 *r*  
 指定要水平地擴大右側的單位數 `CRect`。  
  
 *b*  
 指定要水平地擴大底部的單位數 `CRect`。  
  
### <a name="remarks"></a>備註  
 若要這樣做， `InflateRect` 減去從 left 和 top 的單位，並將單元新增至右側和底部。 參數的 `InflateRect` 簽署值; 正值擴大 `CRect` 、 負值 deflate 它。  
  
 前兩個多載水平地擴大的另一邊的配對 `CRect` 使其總寬度會加上兩次 *x* (或 `cx`) 和總高度會加上兩次 *y* (或 `cy`)。 其他兩個多載水平地擴大的每一端 `CRect` 各自。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#42](../../atl-mfc-shared/codesnippet/CPP/crect-class_8.cpp)]  
  
##  <a name="a-namecrectintersectrecta-crectintersectrect"></a><a name="crect__intersectrect"></a>  CRect::IntersectRect  
 可讓 `CRect` 等於兩個現有矩形的交集。  
  
```  
 
    BOOL IntersectRect(
    LPCRECT 
    lpRect1 ,  
    LPCRECT 
    lpRect2) throw();

 
```  
  
### <a name="parameters"></a>參數  
 `lpRect1`  
 指向 [RECT](../../mfc/reference/rect-structure1.md) 結構或 `CRect` 物件，其中包含來源矩形。  
  
 `lpRect2`  
 指向 `RECT` 結構或 `CRect` 物件，其中包含來源矩形。  
  
### <a name="return-value"></a>傳回值  
 非零，如果交集不是空的。0，表示的交集為空。  
  
### <a name="remarks"></a>備註  
 交集是兩個現有的矩形中包含的最大矩形。  
  
> [!NOTE]
>  這兩個矩形必須正規化，或此函式可能會失敗。 您可以呼叫 [NormalizeRect](#crect__normalizerect) 正規化之前呼叫這個函式的矩形。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#43](../../atl-mfc-shared/codesnippet/CPP/crect-class_9.cpp)]  
  
##  <a name="a-namecrectisrectemptya-crectisrectempty"></a><a name="crect__isrectempty"></a>  CRect::IsRectEmpty  
 決定是否 `CRect` 是空的。  
  
```  
BOOL IsRectEmpty() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果為非零 `CRect` 是空的 0 如果 `CRect` 不是空的。  
  
### <a name="remarks"></a>備註  
 矩形是空白如果寬度或高度都是 0 或負數。 不同於 `IsRectNull`, ，它會決定是否所有矩形的座標都為零。  
  
> [!NOTE]
>  矩形必須正規化，或此函式可能會失敗。 您可以呼叫 [NormalizeRect](#crect__normalizerect) 正規化之前呼叫這個函式的矩形。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#44](../../atl-mfc-shared/codesnippet/CPP/crect-class_10.cpp)]  
  
##  <a name="a-namecrectisrectnulla-crectisrectnull"></a><a name="crect__isrectnull"></a>  CRect::IsRectNull  
 決定是否上、 左、 下方、 以滑鼠右鍵的值和 `CRect` 所有等於 0。  
  
```  
BOOL IsRectNull() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果為非零 `CRect`左上方的底部，並正確的值是所有等於 0，否則為 0。  
  
### <a name="remarks"></a>備註  
 不同於 `IsRectEmpty`, ，決定矩形是否為空白。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#45](../../atl-mfc-shared/codesnippet/CPP/crect-class_11.cpp)]  
  
##  <a name="a-namecrectmovetoxa-crectmovetox"></a><a name="crect__movetox"></a>  CRect::MoveToX  
 呼叫此函式，將矩形移至所指定絕對 x 座標 *x*。  
  
```  
 
void MoveToX(
int   
x) throw();

 
```  
  
### <a name="parameters"></a>參數  
 *x*  
 絕對 x 座標之矩形左上角。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#46](../../atl-mfc-shared/codesnippet/CPP/crect-class_12.cpp)]  
  
##  <a name="a-namecrectmovetoxya-crectmovetoxy"></a><a name="crect__movetoxy"></a>  CRect::MoveToXY  
 呼叫此函式可將矩形移至絕對 x 和 y 座標指定。  
  
```  
 
    void MoveToXY(
    int 
    x ,  
    int 
    y) throw();
void MoveToXY(
    POINT 
    point) throw();

 
```  
  
### <a name="parameters"></a>參數  
 *x*  
 絕對 x 座標之矩形左上角。  
  
 *y*  
 絕對 y 座標之矩形左上角。  
  
 `point`  
 A **點** 結構，指定絕對左上角的矩形。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#47](../../atl-mfc-shared/codesnippet/CPP/crect-class_13.cpp)]  
  
##  <a name="a-namecrectmovetoya-crectmovetoy"></a><a name="crect__movetoy"></a>  CRect::MoveToY  
 呼叫此函式，將矩形移至所指定絕對 y 座標 *y*。  
  
```  
 
void MoveToY(
int   
y) throw();

 
```  
  
### <a name="parameters"></a>參數  
 *y*  
 絕對 y 座標之矩形左上角。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#48](../../atl-mfc-shared/codesnippet/CPP/crect-class_14.cpp)]  
  
##  <a name="a-namecrectnormalizerecta-crectnormalizerect"></a><a name="crect__normalizerect"></a>  Normalizerect  
 正規化 `CRect` 如此高度和寬度都是正數。  
  
```  
void NormalizeRect() throw();
```  
  
### <a name="remarks"></a>備註  
 矩形會正規化為第四個象限位置，Windows 通常使用的座標。 `NormalizeRect` 比較上方和下方的值，並且如果頂端大於底部會交換。 同樣地，它交換的左邊和右邊的值，如果左側大於右側。 此函式時，處理不同的對應模式和反轉矩形。  
  
> [!NOTE]
>  下列 `CRect` 成員函式需要正規化的矩形，才能正常運作︰ [高度](#crect__height), ，[寬度](#crect__width), ，[大小](#crect__size), ，[IsRectEmpty](#crect__isrectempty), ，[PtInRect](#crect__ptinrect), ，[EqualRect](#crect__equalrect), ，[UnionRect](#crect__unionrect), ，[IntersectRect](#crect__intersectrect), ，[SubtractRect](#crect__subtractrect), ，[運算子 = =](#crect__operator__eq_eq), ，[運算子 ！ =](#crect__operator__neq), ，[運算子 &#124;](#crect__operator__or), ，[運算子 &#124; =](#crect__operator__or_eq), ，[運算子 （& s)](#crect__operator__amp_), ，和 [運算子 （& s) =](#crect__operator__amp__eq)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#49](../../atl-mfc-shared/codesnippet/CPP/crect-class_15.cpp)]  
  
##  <a name="a-namecrectoffsetrecta-crectoffsetrect"></a><a name="crect__offsetrect"></a>  CRect::OffsetRect  
 移動 `CRect` 所指定的位移。  
  
```  
 
    void OffsetRect(
    int 
    x ,  
    int 
    y) throw();
void OffsetRect(
    POINT 
    point) throw();
void OffsetRect(
    SIZE 
    size) throw();

 
```  
  
### <a name="parameters"></a>參數  
 *x*  
 指定要向左移動或向右的數量。 它必須是負向左移動。  
  
 *y*  
 指定要上移或下移的數量。 它必須是負數，以向上移動。  
  
 `point`  
 包含 [點](../../mfc/reference/point-structure1.md) 結構或 [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) 物件，指定要移動的兩個維度。  
  
 `size`  
 包含 [大小](http://msdn.microsoft.com/library/windows/desktop/dd145106) 結構或 [CSize](../../atl-mfc-shared/reference/csize-class.md) 物件，指定要移動的兩個維度。  
  
### <a name="remarks"></a>備註  
 移動 `CRect`*x* 沿著 x 軸單位並 *y* 沿著 y 軸的單位。  *x* 和 *y* 參數都是帶正負號的值，因此 `CRect` 可以向左移或向右和向上或向下。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#50](../../atl-mfc-shared/codesnippet/CPP/crect-class_16.cpp)]  
  
##  <a name="a-namecrectoperatorlpcrecta-crectoperator-lpcrect"></a><a name="crect__operator_lpcrect"></a>  CRect::operator LPCRECT  
 將轉換 `CRect` 至 [LPCRECT](../../mfc/reference/data-types-mfc.md)。  
  
'' 運算子 LPCRECT() const throw （);
```  
  
### Remarks  
 When you use this function, you don't need the address-of ( **&**) operator. This operator will be automatically used when you pass a `CRect` object to a function that expects an **LPCRECT**.  
  
### Example  
 [!code-cpp[NVC_ATLMFC_Utilities#58](../../atl-mfc-shared/codesnippet/CPP/crect-class_17.cpp)]  
  
##  <a name="crect__operator_lprect"></a>  CRect::operator LPRECT  
 Converts a `CRect` to an [LPRECT](../../mfc/reference/data-types-mfc.md).  
  
```  operator LPRECT() throw();
```  
  
### <a name="remarks"></a>備註  
 當您使用此函式時，您不需要傳址 ( **&**) 運算子。 當您傳遞時自動使用此運算子 `CRect` 函式的預期物件 `LPRECT`。  
  
### <a name="example"></a>範例  
 請參閱範例 [CRect::operator LPCRECT](#crect__operator_lpcrect)。  
  
##  <a name="a-namecrectoperatoreqa-crectoperator-"></a><a name="crect__operator__eq"></a>  CRect::operator =  
 指派 *srcRect* 到 `CRect`。  
  
```  
 
void operator=(
const RECT& 
srcRect) throw();

 
```  
  
### <a name="parameters"></a>參數  
 *srcRect*  
 是指來源矩形。 可以是 [RECT](../../mfc/reference/rect-structure1.md) 或 `CRect`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#59](../../atl-mfc-shared/codesnippet/CPP/crect-class_18.cpp)]  
  
##  <a name="a-namecrectoperatoreqeqa-crectoperator-"></a><a name="crect__operator__eq_eq"></a>  CRect::operator = =  
 決定是否 `rect` 等於 `CRect` 藉由比較其左上角和右下角的座標。  
  
```  
 
BOOL operator==(
const RECT& 
rect) const throw();

 
```  
  
### <a name="parameters"></a>參數  
 `rect`  
 是指來源矩形。 可以是 [RECT](../../mfc/reference/rect-structure1.md) 或 `CRect`。  
  
### <a name="return-value"></a>傳回值  
 非零，如果相等。否則為 0。  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  這兩個矩形必須正規化，或此函式可能會失敗。 您可以呼叫 [NormalizeRect](#crect__normalizerect) 正規化之前呼叫這個函式的矩形。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#60](../../atl-mfc-shared/codesnippet/CPP/crect-class_19.cpp)]  
  
##  <a name="a-namecrectoperatorneqa-crectoperator-"></a><a name="crect__operator__neq"></a>  CRect::operator ！ =  
 決定是否 `rect` 不等於 `CRect` 藉由比較其左上角和右下角的座標。  
  
```  
 
BOOL operator!=(
const RECT& 
rect) const throw();

 
```  
  
### <a name="parameters"></a>參數  
 `rect`  
 是指來源矩形。 可以是 [RECT](../../mfc/reference/rect-structure1.md) 或 `CRect`。  
  
### <a name="return-value"></a>傳回值  
 非零，如果不相等。否則為 0。  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  這兩個矩形必須正規化，或此函式可能會失敗。 您可以呼叫 [NormalizeRect](#crect__normalizerect) 正規化之前呼叫這個函式的矩形。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#61](../../atl-mfc-shared/codesnippet/CPP/crect-class_20.cpp)]  
  
##  <a name="a-namecrectoperatoraddeqa-crectoperator-"></a><a name="crect__operator__add_eq"></a>  CRect::operator + =  
 前兩個多載移動 `CRect` 所指定的位移。  
  
```  
 
void operator+=(
POINT   
point) throw();

void operator+=(
SIZE   
size) throw();

void operator+=(
LPCRECT   
lpRect) throw();

 
```  
  
### <a name="parameters"></a>參數  
 `point`  
 A [點](../../mfc/reference/point-structure1.md) 結構或 [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) 物件，指定要移動矩形的單位數。  
  
 `size`  
 A [大小](http://msdn.microsoft.com/library/windows/desktop/dd145106) 結構或 [CSize](../../atl-mfc-shared/reference/csize-class.md) 物件，指定要移動矩形的單位數。  
  
 `lpRect`  
 指向 [RECT](../../mfc/reference/rect-structure1.md) 結構或 `CRect` 物件，其中包含要水平地擴大的每一端的單位數 `CRect`。  
  
### <a name="remarks"></a>備註  
 參數的 *x* 和 *y* (或 `cx` 和 `cy`) 值會加入至 `CRect`。  
  
 第三個多載會擴大 `CRect` 單位指定在每個成員的參數數目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#62](../../atl-mfc-shared/codesnippet/CPP/crect-class_21.cpp)]  
  
##  <a name="a-namecrectoperator-eqa-crectoperator--"></a><a name="crect__operator_-_eq"></a>  CRect::operator =  
 前兩個多載移動 `CRect` 所指定的位移。  
  
```  
 
void operator-=(
POINT   
point) throw();

void operator-=(
SIZE   
size) throw();

void operator-=(
LPCRECT   
lpRect) throw();

 
```  
  
### <a name="parameters"></a>參數  
 `point`  
 A [點](../../mfc/reference/point-structure1.md) 結構或 [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) 物件，指定要移動矩形的單位數。  
  
 `size`  
 A [大小](http://msdn.microsoft.com/library/windows/desktop/dd145106) 結構或 [CSize](../../atl-mfc-shared/reference/csize-class.md) 物件，指定要移動矩形的單位數。  
  
 `lpRect`  
 指向 [RECT](../../mfc/reference/rect-structure1.md) 結構或 `CRect` 物件，其中包含要 deflate 的每一端的單位數 `CRect`。  
  
### <a name="remarks"></a>備註  
 參數的 *x* 和 *y* (或 `cx` 和 `cy`) 值會從去掉 `CRect`。  
  
 第三個多載 deflate `CRect` 單位指定在每個成員的參數數目。 請注意，這個多載的運作方式如同 [DeflateRect](#crect__deflaterect)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#63](../../atl-mfc-shared/codesnippet/CPP/crect-class_22.cpp)]  
  
##  <a name="a-namecrectoperatorampeqa-crectoperator-amp"></a><a name="crect__operator__amp__eq"></a>  CRect::operator &amp;=  
 設定 `CRect` 等於交集 `CRect` 和 `rect`。  
  
```  
 
void operator&=(
const RECT& 
rect) throw();

 
```  
  
### <a name="parameters"></a>參數  
 `rect`  
 包含 [RECT](../../mfc/reference/rect-structure1.md) 或 `CRect`。  
  
### <a name="remarks"></a>備註  
 交集是包含在兩個矩形的最大矩形。  
  
> [!NOTE]
>  這兩個矩形必須正規化，或此函式可能會失敗。 您可以呼叫 [NormalizeRect](#crect__normalizerect) 正規化之前呼叫這個函式的矩形。  
  
### <a name="example"></a>範例  
 請參閱範例 [CRect::IntersectRect](#crect__intersectrect)。  
  
##  <a name="a-namecrectoperatororeqa-crectoperator-124"></a><a name="crect__operator__or_eq"></a>  CRect::operator &#124; =  
 設定 `CRect` 等於的聯集 `CRect` 和 `rect`。  
  
```  
 
void operator|=(
const RECT& 
rect) throw();

 
```  
  
### <a name="parameters"></a>參數  
 `rect`  
 包含 `CRect` 或 [RECT](../../mfc/reference/rect-structure1.md)。  
  
### <a name="remarks"></a>備註  
 聯集便是包含兩個來源矩形的最小矩形。  
  
> [!NOTE]
>  這兩個矩形必須正規化，或此函式可能會失敗。 您可以呼叫 [NormalizeRect](#crect__normalizerect) 正規化之前呼叫這個函式的矩形。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#64](../../atl-mfc-shared/codesnippet/CPP/crect-class_23.cpp)]  
  
##  <a name="a-namecrectoperatoradda-crectoperator-"></a><a name="crect__operator__add"></a>  CRect::operator +  
 前兩個多載會傳回 `CRect` 物件，等於 `CRect` 位移指定的位移。  
  
```  
 
CRect operator+(
POINT   
point) const throw();

CRect operator+(
LPCRECT   
lpRect) const throw();

CRect operator+(
SIZE   
size) const throw();

 
```  
  
### <a name="parameters"></a>參數  
 `point`  
 A [點](../../mfc/reference/point-structure1.md) 結構或 [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) 物件，指定要移動的傳回值的單位數。  
  
 `size`  
 A [大小](http://msdn.microsoft.com/library/windows/desktop/dd145106) 結構或 [CSize](../../atl-mfc-shared/reference/csize-class.md) 物件，指定要移動的傳回值的單位數。  
  
 `lpRect`  
 指向 [RECT](../../mfc/reference/rect-structure1.md) 結構或 `CRect` 物件，其中包含要水平地擴大的傳回值的每一端的單位數。  
  
### <a name="return-value"></a>傳回值  
  `CRect` 因移動或人工 `CRect` 參數中指定的單位數。  
  
### <a name="remarks"></a>備註  
 參數的 *x* 和 *y* (或 `cx` 和 `cy`) 會將參數加入至 `CRect`的位置。  
  
 第三個多載會傳回新 `CRect` 等於 `CRect` 膨脹單位指定在每個成員的參數數目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#65](../../atl-mfc-shared/codesnippet/CPP/crect-class_24.cpp)]  
  
##  <a name="a-namecrectoperator-a-crectoperator--"></a><a name="crect__operator_-"></a>  CRect::operator-  
 前兩個多載會傳回 `CRect` 物件，等於 `CRect` 位移指定的位移。  
  
```  
 
CRect operator-(
POINT   
point) const throw();

CRect operator-(
SIZE   
size) const throw();

CRect operator-(
LPCRECT   
lpRect) const throw();

 
```  
  
### <a name="parameters"></a>參數  
 `point`  
 A [點](../../mfc/reference/point-structure1.md) 結構或 `CPoint` 物件，指定要移動的傳回值的單位數。  
  
 `size`  
 A [大小](http://msdn.microsoft.com/library/windows/desktop/dd145106) 結構或 `CSize` 物件，指定要移動的傳回值的單位數。  
  
 `lpRect`  
 指向 [RECT](../../mfc/reference/rect-structure1.md) 結構或 `CRect` 物件，其中包含要 deflate 每一端的傳回值的單位數。  
  
### <a name="return-value"></a>傳回值  
  `CRect` 因移動或升空的方式回應 `CRect` 參數中指定的單位數。  
  
### <a name="remarks"></a>備註  
 參數的 *x* 和 *y* (或 `cx` 和 `cy`) 參數會減去 `CRect`的位置。  
  
 第三個多載會傳回新 `CRect` 等於 `CRect` 縮小單位指定在每個成員的參數數目。 請注意，這個多載的運作方式如同 [DeflateRect](#crect__deflaterect), ，而非 [SubtractRect](#crect__subtractrect)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#66](../../atl-mfc-shared/codesnippet/CPP/crect-class_25.cpp)]  
  
##  <a name="a-namecrectoperatorampa-crectoperator-amp"></a><a name="crect__operator__amp_"></a>  CRect::operator &amp;  
 傳回 `CRect` 也就是交集 `CRect` 和 *rect2*。  
  
```  
 
CRect operator&(
const RECT& 
rect2) const throw();

 
```  
  
### <a name="parameters"></a>參數  
 *rect2*  
 包含 [RECT](../../mfc/reference/rect-structure1.md) 或 `CRect`。  
  
### <a name="return-value"></a>傳回值  
 A `CRect` 也就是交集 `CRect` 和 *rect2*。  
  
### <a name="remarks"></a>備註  
 交集是包含在兩個矩形的最大矩形。  
  
> [!NOTE]
>  這兩個矩形必須正規化，或此函式可能會失敗。 您可以呼叫 [NormalizeRect](#crect__normalizerect) 正規化之前呼叫這個函式的矩形。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#67](../../atl-mfc-shared/codesnippet/CPP/crect-class_26.cpp)]  
  
##  <a name="a-namecrectoperatorora-crectoperator-124"></a><a name="crect__operator__or"></a>  CRect::operator &#124;  
 傳回 `CRect` 也就是聯集的 `CRect` 和 *rect2*。  
  
```  
 
CRect operator|(
const RECT& 
rect2) const throw();

 
```  
  
### <a name="parameters"></a>參數  
 *rect2*  
 包含 [RECT](../../mfc/reference/rect-structure1.md) 或 `CRect`。  
  
### <a name="return-value"></a>傳回值  
 A `CRect` 也就是聯集的 `CRect` 和 *rect2*。  
  
### <a name="remarks"></a>備註  
 聯集便是包含兩個矩形的最小矩形。  
  
> [!NOTE]
>  這兩個矩形必須正規化，或此函式可能會失敗。 您可以呼叫 [NormalizeRect](#crect__normalizerect) 正規化之前呼叫這個函式的矩形。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#68](../../atl-mfc-shared/codesnippet/CPP/crect-class_27.cpp)]  
  
##  <a name="a-namecrectptinrecta-crectptinrect"></a><a name="crect__ptinrect"></a>  CRect::PtInRect  
 判斷指定的點是否位於內 `CRect`。  
  
```  
 
BOOL PtInRect(
POINT   
point) const throw();

 
```  
  
### <a name="parameters"></a>參數  
 `point`  
 包含 [點](../../mfc/reference/point-structure1.md) 結構或 [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) 物件。  
  
### <a name="return-value"></a>傳回值  
 如果這個點位於內為非零 `CRect`，否則為 0。  
  
### <a name="remarks"></a>備註  
 點位於 `CRect` 它位於左方或上方的側邊或內所有的四個邊。 右邊或下面上的點超出 `CRect`。  
  
> [!NOTE]
>  矩形必須正規化，或此函式可能會失敗。 您可以呼叫 [NormalizeRect](#crect__normalizerect) 正規化之前呼叫這個函式的矩形。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#51](../../atl-mfc-shared/codesnippet/CPP/crect-class_28.cpp)]  
  
##  <a name="a-namecrectsetrecta-crectsetrect"></a><a name="crect__setrect"></a>  CRect::SetRect  
 設定維度的 `CRect` 至指定的座標。  
  
```  
 
    void SetRect(
    int 
    x1 ,  
    int 
    y1 ,  
    int 
    x2 ,  
    int 
    y2) throw();

 
```  
  
### <a name="parameters"></a>參數  
 `x1`  
 指定左上角的 x 座標。  
  
 `y1`  
 指定左上角的 y 座標。  
  
 `x2`  
 指定右下角的 x 座標。  
  
 `y2`  
 指定右下角的 y 座標。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#52](../../atl-mfc-shared/codesnippet/CPP/crect-class_29.cpp)]  
  
##  <a name="a-namecrectsetrectemptya-crectsetrectempty"></a><a name="crect__setrectempty"></a>  CRect::SetRectEmpty  
 可讓 `CRect` null 矩形所有座標設定為零。  
  
```  
void SetRectEmpty() throw();
```  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#53](../../atl-mfc-shared/codesnippet/CPP/crect-class_30.cpp)]  
  
##  <a name="a-namecrectsizea-crectsize"></a><a name="crect__size"></a>  CRect::Size  
  `cx` 和 `cy` 成員的傳回值包含高度和寬度 `CRect`。  
  
```  
CSize Size() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 A [CSize](../../atl-mfc-shared/reference/csize-class.md) 物件，其中包含大小 `CRect`。  
  
### <a name="remarks"></a>備註  
 高度或寬度可以是負數。  
  
> [!NOTE]
>  矩形必須正規化，或此函式可能會失敗。 您可以呼叫 [NormalizeRect](#crect__normalizerect) 正規化之前呼叫這個函式的矩形。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#54](../../atl-mfc-shared/codesnippet/CPP/crect-class_31.cpp)]  
  
##  <a name="a-namecrectsubtractrecta-crectsubtractrect"></a><a name="crect__subtractrect"></a>  CRect::SubtractRect  
 可讓維度的 **CRect** 等於減去 `lpRectSrc2` 從 `lpRectSrc1`。  
  
```  
 
    BOOL SubtractRect(
    LPCRECT 
    lpRectSrc1 ,  
    LPCRECT 
    lpRectSrc2) throw();

 
```  
  
### <a name="parameters"></a>參數  
 `lpRectSrc1`  
 指向 [RECT](../../mfc/reference/rect-structure1.md) 結構或 `CRect` 從中矩形是要減去的物件。  
  
 `lpRectSrc2`  
 指向 `RECT` 結構或 `CRect` 指向的物件會將被減去矩形 `lpRectSrc1` 參數。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功則為非零，否則為 0。  
  
### <a name="remarks"></a>備註  
 減法運算是包含所有的點的最小矩形 `lpRectScr1` 所沒有的交集 `lpRectScr1` 和 *lpRectScr2*。  
  
 所指定的矩形 `lpRectSrc1` 會是不變，如果所指定的矩形 `lpRectSrc2` 完全不會重疊所指定的矩形 *lpRectSrc1* 在至少一個的 x 或 y-方向。  
  
 比方說，如果 `lpRectSrc1` 已 10,10 (100,100） 和 `lpRectSrc2` 所 50,50 (150,150），所指矩形 `lpRectSrc1` 就是不變，當函式傳回。 如果 `lpRectSrc1` 是 10,10 (100,100） 和 `lpRectSrc2` 所 50,10 (150,150），不過，該矩形所指 `lpRectSrc1` 會包含座標 （10,10、 50100） 函式傳回時。  
  
 `SubtractRect` 不是相同 [運算子-](#crect__operator_-) 或 [運算子-=](#crect__operator_-_eq)。 這些運算子都曾經呼叫 `SubtractRect`。  
  
> [!NOTE]
>  這兩個矩形必須正規化，或此函式可能會失敗。 您可以呼叫 [NormalizeRect](#crect__normalizerect) 正規化之前呼叫這個函式的矩形。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#55](../../atl-mfc-shared/codesnippet/CPP/crect-class_32.cpp)]  
  
##  <a name="a-namecrecttoplefta-crecttopleft"></a><a name="crect__topleft"></a>  CRect::TopLeft  
 做為參考傳回座標 [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) 物件中包含的 `CRect`。  
  
```  
 
CPoint& TopLeft() throw();

const CPoint& TopLeft() const throw();

 
```  
  
### <a name="return-value"></a>傳回值  
 矩形的左上角的座標。  
  
### <a name="remarks"></a>備註  
 您可以使用此函式，取得或設定矩形的左上角。 指派運算子左邊使用此函式，以設定邊角。  
  
### <a name="example"></a>範例  
 請參閱範例 [CRect::CenterPoint](#crect__centerpoint)。  
  
##  <a name="a-namecrectunionrecta-crectunionrect"></a><a name="crect__unionrect"></a>  CRect::UnionRect  
 可讓維度的 `CRect` 等於兩個來源矩形的聯集。  
  
```  
 
    BOOL UnionRect(
    LPCRECT 
    lpRect1 ,  
    LPCRECT 
    lpRect2) throw();

 
```  
  
### <a name="parameters"></a>參數  
 `lpRect1`  
 指向 [RECT](../../mfc/reference/rect-structure1.md) 或 `CRect` ，其中包含來源矩形。  
  
 `lpRect2`  
 指向 `RECT` 或 `CRect` ，其中包含來源矩形。  
  
### <a name="return-value"></a>傳回值  
 非零，如果聯集不是空的。0，表示聯集是空的。  
  
### <a name="remarks"></a>備註  
 聯集便是包含兩個來源矩形的最小矩形。  
  
 Windows 會忽略空的矩形中維度也就是一個矩形，沒有高度，或其任何的寬度。  
  
> [!NOTE]
>  這兩個矩形必須正規化，或此函式可能會失敗。 您可以呼叫 [NormalizeRect](#crect__normalizerect) 正規化之前呼叫這個函式的矩形。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#56](../../atl-mfc-shared/codesnippet/CPP/crect-class_33.cpp)]  
  
##  <a name="a-namecrectwidtha-crectwidth"></a><a name="crect__width"></a>  CRect::Width  
 計算的寬度 `CRect` 減去右值的左的值。  
  
```  
int Width() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 寬度 `CRect`。  
  
### <a name="remarks"></a>備註  
 寬度可以是負數。  
  
> [!NOTE]
>  矩形必須正規化，或此函式可能會失敗。 您可以呼叫 [NormalizeRect](#crect__normalizerect) 正規化之前呼叫這個函式的矩形。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#57](../../atl-mfc-shared/codesnippet/CPP/crect-class_34.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CPoint 類別](../../atl-mfc-shared/reference/cpoint-class.md)   
 [CSize 類別](../../atl-mfc-shared/reference/csize-class.md)   
 [RECT](../../mfc/reference/rect-structure1.md)


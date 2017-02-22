---
title: "CPoint 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CPoint"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LPPOINT 結構"
  - "POINT 結構"
  - "CPoint 類別"
ms.assetid: a6d4db93-35cc-444d-9221-c3e160f6edaa
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CPoint 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

類似於 Windows `POINT` 結構。  
  
## <a name="syntax"></a>語法  
  
```  
class CPoint : public tagPOINT  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CPoint::CPoint](#cpoint__cpoint)|建構 `CPoint`。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CPoint::Offset](#cpoint__offset)|將值加入 **x** 和 **y** 成員 `CPoint`。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CPoint::operator-](#cpoint__operator_-)|傳回的差異 `CPoint` 和大小或點或兩個點或位移的負數大小的大小差異的否定運算。|  
|[CPoint::operator ！ =](#cpoint__operator__neq)|檢查兩個點之間不相等。|  
|[CPoint::operator +](#cpoint__operator__add)|傳回總和 `CPoint` 和大小或點，或 `CRect` 位移的大小。|  
|[CPoint::operator + =](#cpoint__operator__add_eq)|位移 `CPoint` 藉由新增大小或點。|  
|[CPoint::operator =](CPoint::operator%20-=.xml)|位移 `CPoint` 減去大小或點。|  
|[CPoint::operator = =](#cpoint__operator__eq_eq)|檢查兩個點之間相等。|  
  
## <a name="remarks"></a>備註  
 它也包含成員函式來管理 `CPoint` 和 [點](../../mfc/reference/point-structure1.md) 結構。  
  
 A `CPoint` 物件可以使用的地方 `POINT` 使用結構。 這個類別的 「 大小 」 進行互動的運算子可接受 [ [CSize](../../atl-mfc-shared/reference/csize-class.md) 物件或 [大小](http://msdn.microsoft.com/library/windows/desktop/dd145106) 結構，因為這兩個可以互換。  
  
> [!NOTE]
>  這個類別衍生自 `tagPOINT` 結構。 (名稱 `tagPOINT` 是較不常用的名稱 `POINT` 結構。)這表示的資料成員 `POINT` 結構 `x` 和 `y`, ，可存取的資料成員的 `CPoint`。  
  
> [!NOTE]
>  如需有關共用公用程式類別 (例如 `CPoint`)，請參閱 [共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `tagPOINT`  
  
 `CPoint`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atltypes.h  
  
##  <a name="a-namecpointcpointa-cpointcpoint"></a><a name="cpoint__cpoint"></a>  CPoint::CPoint  
 建構 `CPoint` 物件。  
  
```  
CPoint() throw();

CPoint(
    int initX,  
    int initY) throw();

CPoint(
    POINT initPt) throw();

CPoint(
    SIZE initSize) throw();

CPoint(
    LPARAM dwPoint) throw();
```  
  
### <a name="parameters"></a>參數  
 `initX`  
 指定 `x` 之 `CPoint` 成員的值。  
  
 `initY`  
 指定 `y` 之 `CPoint` 成員的值。  
  
 `initPt`  
 [點](../../mfc/reference/point-structure1.md) 結構或 `CPoint` 指定值，用來初始化 `CPoint`。  
  
 `initSize`  
 [大小](http://msdn.microsoft.com/library/windows/desktop/dd145106) 結構或 [CSize](../../atl-mfc-shared/reference/csize-class.md) 指定值，用來初始化 `CPoint`。  
  
 `dwPoint`  
 將 `x` 成員設定為 `dwPoint` 的低階層文字，並將 `y` 成員設定為 `dwPoint` 的高階層文字。  
  
### <a name="remarks"></a>備註  
 如果未提供引數，`x` 和 `y` 成員都會設定為 0。  
  
### <a name="example"></a>範例  
  
```  
 
CPoint   ptTopLeft(0,
    0);

 
// works from a POINT,
    too  
 
POINT   ptHere;  
ptHere.x = 35;  
ptHere.y = 95;  
 
CPoint   ptMFCHere(ptHere);

 
// works from A SIZE  
 
SIZE   sHowBig;  
sHowBig.cx = 300;  
sHowBig.cy = 10;  
 
CPoint ptMFCBig(sHowBig);

 
// or from a DWORD  
 
DWORD   dwSize;  
dwSize = MAKELONG(35,
    95);

 
CPoint ptFromDouble(dwSize);

ASSERT(ptFromDouble == ptMFCHere);
```  
  
##  <a name="a-namecpointoffseta-cpointoffset"></a><a name="cpoint__offset"></a>  CPoint::Offset  
 將值加入 **x** 和 **y** 成員 `CPoint`。  
  
```  
void Offset(
    int xOffset,  
    int yOffset) throw();

 
    void Offset(
    POINT point) throw();

 
    void Offset(
    SIZE size) throw();
```  
  
### <a name="parameters"></a>參數  
 *xOffset*  
 指定要位移量 **x** 成員 `CPoint`。  
  
 *yOffset*  
 指定要位移量 **y** 成員 `CPoint`。  
  
 `point`  
 指定量 ( [點](../../mfc/reference/point-structure1.md) 或 `CPoint`) 位移 `CPoint`。  
  
 `size`  
 指定量 ( [大小](http://msdn.microsoft.com/library/windows/desktop/dd145106) 或 [CSize](../../atl-mfc-shared/reference/csize-class.md)) 位移 `CPoint`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#28](../../atl-mfc-shared/codesnippet/CPP/cpoint-class_1.cpp)]  
  
##  <a name="a-namecpointoperatoreqeqa-cpointoperator-"></a><a name="cpoint__operator__eq_eq"></a>  CPoint::operator = =  
 檢查兩個點之間相等。  
  
```  
BOOL operator==(POINT point) const throw();
```  
  
### <a name="parameters"></a>參數  
 `point`  
 包含 [點](../../mfc/reference/point-structure1.md) 結構或 `CPoint` 物件。  
  
### <a name="return-value"></a>傳回值  
 非零的點是否相等。否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#29](../../atl-mfc-shared/codesnippet/CPP/cpoint-class_2.cpp)]  
  
##  <a name="a-namecpointoperatorneqa-cpointoperator-"></a><a name="cpoint__operator__neq"></a>  CPoint::operator ！ =  
 檢查兩個點之間不相等。  
  
```  
BOOL operator!=(POINT point) const throw();
```  
  
### <a name="parameters"></a>參數  
 `point`  
 包含 [點](../../mfc/reference/point-structure1.md) 結構或 `CPoint` 物件。  
  
### <a name="return-value"></a>傳回值  
 非零，如果點不相等。否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#30](../../atl-mfc-shared/codesnippet/CPP/cpoint-class_3.cpp)]  
  
##  <a name="a-namecpointoperatoraddeqa-cpointoperator-"></a><a name="cpoint__operator__add_eq"></a>  CPoint::operator + =  
 第一個多載會加入將大小為 `CPoint`。  
  
```  
void operator+=(SIZE size) throw();

 
    void operator+=(POINT point) throw();
```  
  
### <a name="parameters"></a>參數  
 `size`  
 包含 [大小](http://msdn.microsoft.com/library/windows/desktop/dd145106) 結構或 [CSize](../../atl-mfc-shared/reference/csize-class.md) 物件。  
  
 `point`  
 包含 [點](../../mfc/reference/point-structure1.md) 結構或 [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) 物件。  
  
### <a name="remarks"></a>備註  
 第二個多載會加入指向 `CPoint`。  
  
 在這兩種情況下，除了透過加入 **x** (或 **cx**) 成員右運算元的 **x** 的成員 `CPoint` 並加入 **y** (或 **cy**) 成員右運算元的 **y** 的成員 `CPoint`。  
  
 例如，加入 `CPoint(5, -7)` 給變數，其中包含 `CPoint(30, 40)` 變更變數 `CPoint(35, 33)`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#31](../../atl-mfc-shared/codesnippet/CPP/cpoint-class_4.cpp)]  
  
##  <a name="a-namecpointoperator-eqa-cpointoperator--"></a><a name="cpoint__operator_-_eq"></a>  CPoint::operator =  
 第一個多載減去從大小 `CPoint`。  
  
```  
void operator-=(SIZE size) throw();

 
    void operator-=(POINT point) throw();
```  
  
### <a name="parameters"></a>參數  
 `size`  
 包含 [大小](http://msdn.microsoft.com/library/windows/desktop/dd145106) 結構或 [CSize](../../atl-mfc-shared/reference/csize-class.md) 物件。  
  
 `point`  
 包含 [點](../../mfc/reference/point-structure1.md) 結構或 [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) 物件。  
  
### <a name="remarks"></a>備註  
 第二個多載減去點從 `CPoint`。  
  
 在這兩種情況下，減法透過減去 **x** (或 **cx**) 成員從右方運算元的 **x** 成員 `CPoint` 減去 **y** (或 **cy**) 成員從右方運算元的 **y** 成員 `CPoint`。  
  
 例如，減去 `CPoint(5, -7)` 變數，其中包含從 `CPoint(30, 40)` 變更變數 `CPoint(25, 47)`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#32](../../atl-mfc-shared/codesnippet/CPP/cpoint-class_5.cpp)]  
  
##  <a name="a-namecpointoperatoradda-cpointoperator-"></a><a name="cpoint__operator__add"></a>  CPoint::operator +  
 使用這個運算子來位移 `CPoint` 由 `CPoint` 或 `CSize` 物件，或位移 `CRect` 由 `CPoint`。  
  
```  
CPoint operator+(SIZE size) const throw();

 
    CPoint operator+(POINT point) const throw();

 
    CRect operator+(const RECT* lpRect) const throw();
```  
  
### <a name="parameters"></a>參數  
 `size`  
 包含 [大小](http://msdn.microsoft.com/library/windows/desktop/dd145106) 結構或 [CSize](../../atl-mfc-shared/reference/csize-class.md) 物件。  
  
 `point`  
 包含 [點](../../mfc/reference/point-structure1.md) 結構或 [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) 物件。  
  
 `lpRect`  
 包含一個指向 [RECT](../../mfc/reference/rect-structure1.md) 結構或 [CRect](../../atl-mfc-shared/reference/crect-class.md) 物件。  
  
### <a name="return-value"></a>傳回值  
 A `CPoint` 大小、 位移 **CPoint** 點，位移或 **CRect** 依點位移。  
  
### <a name="remarks"></a>備註  
 例如，使用前兩個多載來彌補點 `CPoint(25, -19)` 點 `CPoint(15, 5)` 或大小 `CSize(15, 5)` 傳回的值 `CPoint(40, -14)`。  
  
 將矩形加入至某個點之後的位移，傳回矩形 **x** 和 **y** 點中指定的值。 例如，使用最後一個多載來彌補矩形 `CRect(125, 219, 325, 419)` 點 `CPoint(25, -19)` 傳回 `CRect(150, 200, 350, 400)`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#33](../../atl-mfc-shared/codesnippet/CPP/cpoint-class_6.cpp)]  
  
##  <a name="a-namecpointoperator-a-cpointoperator--"></a><a name="cpoint__operator_-"></a>  CPoint::operator-  
 使用前兩個多載減去 `CPoint` 或 `CSize` 物件從 `CPoint`。  
  
```  
CSize operator-(POINT point) const throw();

 
    CPoint operator-(SIZE size) const throw();

 
    CRect operator-(const RECT* lpRect) const throw();

 
    CPoint operator-() const throw();
```  
  
### <a name="parameters"></a>參數  
 `point`  
 A [點](../../mfc/reference/point-structure1.md) 結構或 [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) 物件。  
  
 `size`  
 A [大小](http://msdn.microsoft.com/library/windows/desktop/dd145106) 結構或 [CSize](../../atl-mfc-shared/reference/csize-class.md) 物件。  
  
 `lpRect`  
 指標 [RECT](../../mfc/reference/rect-structure1.md) 結構或 [CRect](../../atl-mfc-shared/reference/crect-class.md) 物件。  
  
### <a name="return-value"></a>傳回值  
 A `CSize` 也就是兩個點之間的差異 `CPoint` 的大小，否定位移 `CRect` 否定點的位移或 `CPoint` 也就是一個點的否定運算。  
  
### <a name="remarks"></a>備註  
 第三個多載位移 `CRect` 否定的 `CPoint`。 最後，使用要變換正負號的一元運算子 `CPoint`。  
  
 例如，使用第一個多載來尋找兩個點之間的差異 `CPoint(25, -19)` 和 `CPoint(15, 5)` 傳回 `CSize(10, -24)`。  
  
 減去 `CSize` 從 `CPoint` 並未與上述相同的計算，但是會傳回 `CPoint` 物件無法 `CSize` 物件。 例如，使用第二個多載來尋找點之間的差異 `CPoint(25, -19)` 和大小 `CSize(15, 5)` 傳回 `CPoint(10, -24)`。  
  
 減去矩形從點傳回的矩形位移的否定 **x** 和 **y** 點中指定的值。 例如，使用最後一個多載來彌補矩形 `CRect(125, 200, 325, 400)` 點 `CPoint(25, -19)` 傳回 `CRect(100, 219, 300, 419)`。  
  
 若要取消點使用一元運算子。 例如，使用一元運算子的點 `CPoint(25, -19)` 傳回 `CPoint(-25, 19)`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#34](../../atl-mfc-shared/codesnippet/CPP/cpoint-class_7.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 MDI](../../top/visual-cpp-samples.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [POINT 結構](../../mfc/reference/point-structure1.md)   
 [CRect 類別](../../atl-mfc-shared/reference/crect-class.md)   
 [CSize 類別](../../atl-mfc-shared/reference/csize-class.md)




---
title: "CSize 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSize
- ATLTYPES/ATL::CSize
- ATLTYPES/ATL::CSize::CSize
dev_langs: C++
helpviewer_keywords:
- SIZE
- dimensions, MFC
- dimensions
- CSize class
ms.assetid: fb2cf85a-0bc1-46f8-892b-309c108b52ae
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ac18decc8a2bb6bbc2d9e9677640eba67c85077e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="csize-class"></a>CSize 類別
類似於實作相對座標或位置的 Windows [SIZE](http://msdn.microsoft.com/library/windows/desktop/dd145106) 結構。  
  
## <a name="syntax"></a>語法  
  
```  
class CSize : public tagSIZE 
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CSize::CSize](#csize)|建構 `CSize` 物件。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CSize::operator-](#operator_-)|減去兩個大小。|  
|[CSize::operator ！ =](#operator_neq)|檢查相等`CSize`和大小。|  
|[CSize::operator +](#operator_add)|將兩個大小。|  
|[CSize::operator + =](#operator_add_eq)|將大小`CSize`。|  
|[CSize::operator =](#operator_-_eq)|將來自大小減去`CSize`。|  
|[CSize::operator = =](#operator_eq_eq)|檢查是否相等`CSize`和大小。|  
  
## <a name="remarks"></a>備註  
 這個類別衍生自**大小**結構。 這表示您可以傳遞`CSize`中呼叫的參數**大小**的資料成員**大小**結構是可存取的資料成員的`CSize`。  
  
 **Cx**和**cy**成員**大小**(和`CSize`) 都是公用的。 此外，`CSize`實作成員函式來管理**大小**結構。  
  
> [!NOTE]
>  如需有關共用 公用程式類別 (例如`CSize`)，請參閱[共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `tagSIZE`  
  
 `CSize`  
  
## <a name="requirements"></a>需求  
 **標頭：** atltypes.h  
  
##  <a name="csize"></a>CSize::CSize  
 建構 `CSize` 物件。  
  
```  
CSize() throw();
CSize( int initCX, int initCY) throw();
CSize( SIZE initSize) throw();
CSize( POINT initPt) throw();
CSize( DWORD dwSize) throw(); 
```  
  
### <a name="parameters"></a>參數  
 *initCX*  
 設定**cx**成員`CSize`。  
  
 *initCY*  
 設定**cy**成員`CSize`。  
  
 `initSize`  
 [大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)結構或`CSize`用來初始化物件`CSize`。  
  
 `initPt`  
 [點](../../mfc/reference/point-structure1.md)結構或`CPoint`用來初始化物件`CSize`。  
  
 `dwSize`  
 `DWORD`用來初始化`CSize`。 低序位字組是**cx**成員且高序位文字已**cy**成員。  
  
### <a name="remarks"></a>備註  
 如果任何引數不指定**cx**和**cy**初始化為零。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#97](../../atl-mfc-shared/codesnippet/cpp/csize-class_1.cpp)]  
  
##  <a name="operator_eq_eq"></a>CSize::operator = =  
 這兩個大小相等檢查。  
  
```   
BOOL operator==(SIZE size) const throw(); 
```  
  
### <a name="remarks"></a>備註  
 傳回的大小是否相等則為非零，otherwize 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#98](../../atl-mfc-shared/codesnippet/cpp/csize-class_2.cpp)]  
  
##  <a name="operator_neq"></a>CSize::operator ！ =  
 這兩個大小相等檢查。  
  
```   
BOOL operator!=(SIZE size) const throw(); 
```  
  
### <a name="remarks"></a>備註  
 傳回的大小是否不相等，則為非零，否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#99](../../atl-mfc-shared/codesnippet/cpp/csize-class_3.cpp)]  
  
##  <a name="operator_add_eq"></a>CSize::operator + =  
 新增至該大小`CSize`。  
  
```   
void operator+=(SIZE size) throw(); 
```  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#100](../../atl-mfc-shared/codesnippet/cpp/csize-class_4.cpp)]  
  
##  <a name="operator_-_eq"></a>CSize::operator =  
 將從這個大小減去`CSize`。  
  
```   
void operator-=(SIZE size) throw(); 
```  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#101](../../atl-mfc-shared/codesnippet/cpp/csize-class_5.cpp)]  
  
##  <a name="operator_add"></a>CSize::operator +  
 這些運算子加入`CSize`值參數的值。  
  
```   
CSize operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw(); 
```  
  
### <a name="remarks"></a>備註  
 請參閱下列說明的個別運算子：  
  
- **運算子 + (** `size` **)**這項作業會加入兩個`CSize`值。  
  
- **運算子 + (** `point` **)**這項作業的位移 （移動）[點](http://msdn.microsoft.com/library/windows/desktop/dd162805)(或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)) 值由此`CSize`值。 **Cx**和**cy** this 的成員`CSize`值會加入至**x**和**y**資料成員**點**值。 它相當於新版[CPoint::operator +](../../atl-mfc-shared/reference/cpoint-class.md#operator_add)採用[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)參數。  
  
- **運算子 + (** `lpRect` **)**這項作業的位移 （移動） [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) (或[CRect](../../atl-mfc-shared/reference/crect-class.md)) 值由此`CSize`值。 **Cx**和**cy** this 的成員`CSize`值會加入至**左**，**頂端**，**右邊**，和**底部**資料成員`RECT`值。 它相當於新版[CRect::operator +](../../atl-mfc-shared/reference/crect-class.md#operator_add)採用[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)參數。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#102](../../atl-mfc-shared/codesnippet/cpp/csize-class_6.cpp)]  
  
##  <a name="operator_-"></a>CSize::operator-  
 這些運算子的前三個減去此`CSize`值參數的值。  
  
```   
CSize operator-(SIZE size) const throw();
CPoint operator-(POINT point) const throw();
CRect operator-(const RECT* lpRect) const throw();
CSize operator-() const throw(); 
```  
  
### <a name="remarks"></a>備註  
 第四個運算子，也就是一元減號，變更的正負號`CSize`值。 請參閱下列說明的個別運算子：  
  
- **運算子-(** `size` **)**這項作業，減去兩個`CSize`值。  
  
- **運算子-(** `point` **)**這項作業的位移 （移動）[點](http://msdn.microsoft.com/library/windows/desktop/dd162805)或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)加法反元素，這個值`CSize`值。 **Cx**和**cy**這個`CSize`值都會從減去**x**和**y**資料成員**點**值。 它相當於新版[CPoint::operator-](../../atl-mfc-shared/reference/cpoint-class.md#operator_-)採用[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)參數。  
  
- **運算子-(** `lpRect` **)**這項作業的位移 （移動） [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)或[CRect](../../atl-mfc-shared/reference/crect-class.md)加法反元素，這個值`CSize`值。 **Cx**和**cy** this 的成員`CSize`值都會從減去**左**，**頂端**，**右邊**，和**底部**資料成員`RECT`值。 它相當於新版[CRect::operator-](../../atl-mfc-shared/reference/crect-class.md#operator_-)採用[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)參數。  
  
- **運算子-（)**此操作會傳回這個加法反元素`CSize`值。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#103](../../atl-mfc-shared/codesnippet/cpp/csize-class_7.cpp)]  
  
## <a name="see-also"></a>請參閱  
 [MFC 範例 MDI](../../visual-cpp-samples.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CRect 類別](../../atl-mfc-shared/reference/crect-class.md)   
 [CPoint 類別](../../atl-mfc-shared/reference/cpoint-class.md)


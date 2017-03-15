---
title: "CMFCDynamicLayout 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: c2df2976-f049-47fc-9cf0-abe3e01948bc
caps.latest.revision: 16
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 3066da5e1f874c2f0f2a2564b15582d7238c539b
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcdynamiclayout-class"></a>CMFCDynamicLayout 類別
指定使用者調整視窗大小時，控制項在視窗中如何移動和調整大小。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCDynamicLayout : public CObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|`CMFCDynamicLayout::CMFCDynamicLayout`|建構 `CMFCDynamicLayout` 物件。|  
|`CMFCDynamicLayout::~CMFCDynamicLayout`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCDynamicLayout::AddItem](#additem)|將子視窗 (通常是控制項) 加入至動態配置管理員所控制的視窗清單。|  
|[CMFCDynamicLayout::Adjust](#adjust)|將子視窗 (通常是控制項) 加入至動態配置管理員所控制的視窗清單。|  
|[CMFCDynamicLayout::Create](#create)|儲存並驗證主控視窗。|  
|[CMFCDynamicLayout::GetHostWnd](#gethostwnd)|傳回主控視窗的指標。|  
|[CMFCDynamicLayout::GetMinSize](#getminsize)|傳回視窗大小下限，低於此值就不調整版面配置。|  
|[CMFCDynamicLayout::GetWindowRect](#getwindowrect)|擷取視窗的目前用戶端區域的週框。|  
|[CMFCDynamicLayout::HasItem](#hasitem)|檢查如果子控制項是否已加入動態配置。|  
|[CMFCDynamicLayout::IsEmpty](#isempty)|檢查動態配置是否未加入任何子視窗。|  
|[CMFCDynamicLayout::LoadResource](#loadresource)|從 AFX_DIALOG_LAYOUT 資源讀取動態配置，然後將配置套用至主控視窗。|  
|靜態[CMFCDynamicLayout::MoveHorizontal](#movehorizontal)|取得[MoveSettings](#movesettings_structure)定義當使用者調整其裝載的視窗水平移動多少的子控制項的值。|  
|靜態[CMFCDynamicLayout::MoveHorizontalAndVertical](#movehorizontalandvertical)|取得[MoveSettings](#movesettings_structure)定義當使用者調整其裝載的視窗水平移動多少的子控制項的值。|  
|靜態[CMFCDynamicLayout::MoveNone](#movenone)|取得[MoveSettings](#movesettings_structure)值，表示沒有動畫，而垂直或水平時，子控制項。|  
|靜態[CMFCDynamicLayout::MoveVertical](#movevertical)|取得[MoveSettings](#movesettings_structure)定義當使用者調整其裝載的視窗垂直移動多少的子控制項的值。|  
|[CMFCDynamicLayout::SetMinSize](#setminsize)|設定視窗大小下限，低於此值就不調整版面配置。|  
|靜態[CMFCDynamicLayout::SizeHorizontal](#sizehorizontal)|取得[SizeSettings](#sizesettings_structure)定義當使用者調整其裝載的視窗水平調整多少的子控制項的值。|  
|靜態[CMFCDynamicLayout::SizeHorizontalAndVertical](#sizehorizontalandvertical)|取得[SizeSettings](#sizesettings_structure)定義當使用者調整其裝載的視窗水平調整多少的子控制項的值。|  
|靜態[CMFCDynamicLayout::SizeNone](#sizenone)|取得[SizeSettings](#sizesettings_structure)值，表示子控制項的大小沒有變更。|  
|靜態[CMFCDynamicLayout::SizeVertical](#sizevertical)|取得[SizeSettings](#sizesettings_structure)定義當使用者調整其裝載的視窗垂直調整多少的子控制項的值。|  
  
## <a name="nested-types"></a>巢狀類型  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCDynamicLayout::MoveSettings 結構](#movesettings_structure)|為動態配置中控制項封裝移動資料。|  
|[CMFCDynamicLayout::SizeSettings 結構](#sizesettings_structure)|為動態配置中的控制項封裝大小變更資料。|  
  
## <a name="remarks"></a>備註  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCDynamicLayout](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxlayout.h  
  
##  <a name="a-nameadditema--cmfcdynamiclayoutadditem"></a><a name="additem"></a>CMFCDynamicLayout::AddItem  
 將子視窗 (通常是控制項) 加入至動態配置管理員所控制的視窗清單。  
  
```  
BOOL AddItem(
    HWND hwnd,
    MoveSettings moveSettings SizeSettings sizeSettings);

 
BOOL AddItem(
    int nID,
    MoveSettings moveSettings SizeSettings sizeSettings);
```  
  
### <a name="parameters"></a>參數  
 `hwnd`  
 要加入之視窗的控制代碼。  
  
 `nID`  
 要加入之子控制項的 ID。  
  
 `moveSettings`  
 說明在視窗大小變更時應如何移動控制項的結構。  
  
 `sizeSettings`  
 說明在視窗大小變更時應如何為控制項調整大小的結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功加入項目則為 True，否則為 False。  
  
### <a name="remarks"></a>備註  
 調整主控視窗的大小時，子控制項的位置和大小會動態變更。  
  
##  <a name="a-nameadjusta--cmfcdynamiclayoutadjust"></a><a name="adjust"></a>CMFCDynamicLayout::Adjust  
 將子視窗 (通常是控制項) 加入至動態配置管理員所控制的視窗清單。  
  
```  
void Adjust();
```  
  
### <a name="remarks"></a>備註  
 調整主控視窗的大小時，子控制項的位置和大小會動態變更。  
  
##  <a name="a-namecreatea--cmfcdynamiclayoutcreate"></a><a name="create"></a>CMFCDynamicLayout::Create  
 儲存並驗證主控視窗。  
  
```  
BOOL Create(CWnd* pHostWnd);
```  
  
### <a name="parameters"></a>參數  
 pHostWnd  
 主控視窗的指標。  
  
### <a name="return-value"></a>傳回值  
 如果作業成功，則為 TRUE，否則為 FALSE。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegethostwnda--cmfcdynamiclayoutgethostwnd"></a><a name="gethostwnd"></a>CMFCDynamicLayout::GetHostWnd  
 傳回主控視窗的指標。  
  
```  
CWnd* GetHostWnd();
```  
  
### <a name="return-value"></a>傳回值  
 主控視窗的指標。  
  
### <a name="remarks"></a>備註  
 根據預設，會重新計算所有子控制項相對於此視窗的位置。  
  
##  <a name="a-namegetminsizea--cmfcdynamiclayoutgetminsize"></a><a name="getminsize"></a>CMFCDynamicLayout::GetMinSize  
 傳回視窗大小下限，低於此值就不調整版面配置。  
  
```  
CSize GetMinSize();
```  
  
### <a name="return-value"></a>傳回值  
 視窗大小下限，低於此值就不調整版面配置。  
  
### <a name="remarks"></a>備註  
 調整主控視窗的大小時，子控制項的位置和大小會動態變更，但是有大小下限，低於此值就不會調整版面配置。 使用者可以將視窗調小，但視窗的某些部分就看不見。  
  
##  <a name="a-namegetwindowrecta--cmfcdynamiclayoutgetwindowrect"></a><a name="getwindowrect"></a>CMFCDynamicLayout::GetWindowRect  
 擷取視窗的目前用戶端區域的週框。  
  
```  
void GetHostWndRect(CRect& rect,);
```  
  
### <a name="parameters"></a>參數  
 `rect`  
 在此函數傳回之後，此參數會包含版面配置區域的週框。 這是輸出參數；輸入值會被覆寫。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namehasitema--cmfcdynamiclayouthasitem"></a><a name="hasitem"></a>CMFCDynamicLayout::HasItem  
 檢查如果子控制項是否已加入動態配置。  
  
```  
BOOL HasItem(HWND hwnd);
```  
  
### <a name="parameters"></a>參數  
 `hwnd`  
 控制項的視窗控制代碼。  
  
### <a name="return-value"></a>傳回值  
 如果配置已有此項目，則為 TRUE，否則為 FALSE。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameisemptya--cmfcdynamiclayoutisempty"></a><a name="isempty"></a>CMFCDynamicLayout::IsEmpty  
 檢查動態配置是否未加入任何子視窗。  
  
```  
BOOL IsEmpty();
```  
  
### <a name="return-value"></a>傳回值  
 如果配置沒有任何項目，則為 TRUE，否則為 FALSE。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameloadresourcea--cmfcdynamiclayoutloadresource"></a><a name="loadresource"></a>CMFCDynamicLayout::LoadResource  
 從 AFX_DIALOG_LAYOUT 資源讀取動態配置，然後將配置套用至主控視窗。  
  
```  
static BOOL LoadResource(CWnd* pHostWnd,
    LPVOID lpResource,
    DWORD dwSize);  
```  
  
### <a name="parameters"></a>參數  
 `pHostWnd`  
 主控視窗的指標。  
  
 `lpResource`  
 包含 AFX_DIALOG_LAYOUT 資源的緩衝區的指標。  
  
 `dwSize`  
 緩衝區大小，以位元組為單位。  
  
### <a name="return-value"></a>傳回值  
 如果載入資源並將其套用至主控視窗中，則為 TRUE，否則為 FALSE。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namemovehorizontala--cmfcdynamiclayoutmovehorizontal"></a><a name="movehorizontal"></a>CMFCDynamicLayout::MoveHorizontal  
 取得[MoveSettings](#movesettings_structure)定義當使用者調整其裝載的視窗水平移動多少的子控制項的值。  
  
```  
static MoveSettings MoveHorizontal(int nRatio);  
```  
  
### <a name="parameters"></a>參數  
 `nRatio`  
 定義當使用者調整主視窗大小時，水平移動子控制項的幅度百分比。  
  
### <a name="return-value"></a>傳回值  
 A [MoveSettings](#movesettings_structure)封裝所要求的值移比率。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namemovehorizontalandverticala--cmfcdynamiclayoutmovehorizontalandvertical"></a><a name="movehorizontalandvertical"></a>CMFCDynamicLayout::MoveHorizontalAndVertical  
 取得[MoveSettings](#movesettings_structure)定義當使用者調整其裝載的視窗水平移動多少的子控制項的值。  
  
```  
static MoveSettings MoveHorizontalAndVertical(int nXRatio int nYRatio);  
```  
  
### <a name="parameters"></a>參數  
 `nXRatio`  
 定義當使用者調整主視窗大小時，水平移動子控制項的幅度百分比。  
  
 `nYRatio`  
 定義當使用者調整主視窗大小時，垂直移動子控制項的幅度百分比。  
  
### <a name="return-value"></a>傳回值  
 A [MoveSettings](#movesettings_structure)封裝所要求的值移比率。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namemovenonea--cmfcdynamiclayoutmovenone"></a><a name="movenone"></a>CMFCDynamicLayout::MoveNone  
 取得[MoveSettings](#movesettings_structure)值，表示沒有動畫，而垂直或水平時，子控制項。  
  
```  
static MoveSettings MoveNone();  
```  
  
### <a name="return-value"></a>傳回值  
 A [MoveSettings](#movesettings_structure)的位置，固定控制項，以便不會移動時使用者重新調整大小的主視窗的值。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namemovesettingsstructurea--cmfcdynamiclayoutmovesettings-structure"></a><a name="movesettings_structure"></a>CMFCDynamicLayout::MoveSettings 結構  
 為動態配置中控制項封裝移動資料。  
  
```  
struct CMFCDynamicLayout::MoveSettings;  
```  
  
### <a name="remarks"></a>備註  
 這是 `CMFCDynamicLayout` 內部的巢狀類別。  

## <a name="cmfcdynamiclayoutmovesettingsishorizontal"></a>CMFCDynamicLayout::MoveSettings::IsHorizontal
檢查移動資料是否指定非零的水平移動。  
  

```  
BOOL IsHorizontal() const 
```  
  
## <a name="return-value"></a>傳回值  
 如果 `MoveSettings` 物件指定非零的水平移動，則為 TRUE。  

 ## <a name="cmfcdynamiclayoutmovesettingsisnone"></a>CMFCDynamicLayout::MoveSettings::IsNone
 檢查移動資料是否指定不移動。  
  
```  
BOOL IsNone() const 
```  
  
## <a name="return-value"></a>傳回值  
 如果 `MoveSettings` 物件指定不移動，則為 TRUE 。  

## <a name="cmfcdynamiclayoutmovesettingsisvertical"></a>CMFCDynamicLayout::MoveSettings::IsVertical
  請檢查移動資料是否指定非零的垂直移動。  
  
```  
BOOL IsVertical() const 
```  
  
## <a name="return-value"></a>傳回值  
 如果 `MoveSettings` 物件指定非零的垂直移動，則為 TRUE。  

##  <a name="a-namemoveverticala--cmfcdynamiclayoutmovevertical"></a><a name="movevertical"></a>CMFCDynamicLayout::MoveVertical  
 取得[MoveSettings](#movesettings_structure)定義當使用者調整其裝載的視窗垂直移動多少的子控制項的值。  
  
```  
static MoveSettings MoveVertical(int nRatio);  
```  
  
### <a name="parameters"></a>參數  
 `nRatio`  
 定義當使用者調整主視窗大小時，垂直移動子控制項的幅度百分比。  
  
### <a name="return-value"></a>傳回值  
 A [MoveSettings](#movesettings_structure)封裝所要求的值移比率。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetminsizea--cmfcdynamiclayoutsetminsize"></a><a name="setminsize"></a>CMFCDynamicLayout::SetMinSize  
 設定視窗大小下限，低於此值就不調整版面配置。  
  
```  
void SetMinSize(const CSize& size);
```  
  
### <a name="parameters"></a>參數  
 `size`  
 所需的大小下限，低於此值就不調整版面配置。  
  
### <a name="remarks"></a>備註  
 調整主控視窗的大小時，子控制項的位置和大小會動態變更，但是有大小下限，低於此值就不會調整版面配置。 使用者可以將視窗調小，但視窗的某些部分就看不見。  
  
##  <a name="a-namesizehorizontala--cmfcdynamiclayoutsizehorizontal"></a><a name="sizehorizontal"></a>CMFCDynamicLayout::SizeHorizontal  
 取得[SizeSettings](#sizesettings_structure)定義當使用者調整其裝載的視窗水平調整多少的子控制項的值。  
  
```  
static SizeSettings SizeHorizontal(int nRatio);  
```  
  
### <a name="parameters"></a>參數  
 `nRatio`  
 定義當使用者調整主視窗大小時，水平調整子控制項大小的幅度百分比。  
  
### <a name="return-value"></a>傳回值  
 A [SizeSettings](#sizesettings_structure)封裝要求的大小比例的值。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesizehorizontalandverticala--cmfcdynamiclayoutsizehorizontalandvertical"></a><a name="sizehorizontalandvertical"></a>CMFCDynamicLayout::SizeHorizontalAndVertical  
 取得[SizeSettings](#sizesettings_structure)定義當使用者調整其裝載的視窗水平調整多少的子控制項的值。  
  
```  
static SizeSettings SizeHorizontalAndVertical(int nXRatio int nYRatio);  
```  
  
### <a name="parameters"></a>參數  
 `nXRatio`  
 定義當使用者調整主視窗大小時，水平調整子控制項大小的幅度百分比。  
  
 `nYRatio`  
 定義當使用者調整主視窗大小時，垂直調整子控制項大小的幅度百分比。  
  
### <a name="return-value"></a>傳回值  
 A [SizeSettings](#sizesettings_structure)封裝要求的大小比例的值。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesizenonea--cmfcdynamiclayoutsizenone"></a><a name="sizenone"></a>CMFCDynamicLayout::SizeNone  
 取得[SizeSettings](#sizesettings_structure)值，表示子控制項的大小沒有變更。  
  
```  
static SizeSettings SizeNone();  
```  
  
### <a name="return-value"></a>傳回值  
 A [SizeSettings](#sizesettings_structure)控制項修正特定大小，使它不會變更大小，當使用者調整主應用程式視窗的值。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesizesettingsstructurea--cmfcdynamiclayoutsizesettings-structure"></a><a name="sizesettings_structure"></a>CMFCDynamicLayout::SizeSettings 結構  
 為動態配置中的控制項封裝大小變更資料。  
  
```  
struct CMFCDynamicLayout::SizeSettings;  
```  
  
### <a name="remarks"></a>備註  
 這是 `CMFCDynamicLayout` 內部的巢狀類別。  

## <a name="cmfcdynamiclayoutsizesettingsishorizontal"></a>CMFCDynamicLayout::SizeSettings::IsHorizontal
檢查調整大小資料是否指定非零的水平調整大小。  
  
```  
BOOL IsHorizontal() const 
```  
  
## <a name="return-value"></a>傳回值  
 如果 `SizeSettings` 物件指定非零的水平調整大小，則為 TRUE。 

## <a name="cmfcdynamiclayoutsizesettingsisnone"></a>CMFCDynamicLayout::SizeSettings::IsNone
檢查調整大小資料是否指定不調整大小。  
  
```  
BOOL IsNone() const 
```  
  
## <a name="return-value"></a>傳回值  
 如果 `SizeSettings` 物件指定不調整大小，則為 TRUE 。  

## <a name="cmfcdynamiclayoutsizesettingsisvertical"></a>CMFCDynamicLayout::SizeSettings::IsVertical
檢查調整大小資料是否指定非零的垂直調整大小。  
  
```  
BOOL IsVertical() const 
```  
  
## <a name="return-value"></a>傳回值  
 如果 `SizeSettings` 物件指定非零的垂直調整大小，則為 TRUE。  

##  <a name="a-namesizeverticala--cmfcdynamiclayoutsizevertical"></a><a name="sizevertical"></a>CMFCDynamicLayout::SizeVertical  
 取得[SizeSettings](#sizesettings_structure)定義當使用者調整其裝載的視窗垂直調整多少的子控制項的值。  
  
```  
static SizeSettings SizeVertical(int nRatio);  
```  
  
### <a name="parameters"></a>參數  
 `nRatio`  
 定義當使用者調整主視窗大小時，垂直調整子控制項大小的幅度百分比。  
  
### <a name="return-value"></a>傳回值  
 A [SizeSettings](#sizesettings_structure)封裝要求的大小比例的值。  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)


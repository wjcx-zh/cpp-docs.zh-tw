---
title: "CMFCDynamicLayout 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCDynamicLayout
- AFXLAYOUT/CMFCDynamicLayout
- AFXLAYOUT/CMFCDynamicLayout::AddItem
- AFXLAYOUT/CMFCDynamicLayout::Adjust
- AFXLAYOUT/CMFCDynamicLayout::Create
- AFXLAYOUT/CMFCDynamicLayout::GetHostWnd
- AFXLAYOUT/CMFCDynamicLayout::GetMinSize
- AFXLAYOUT/CMFCDynamicLayout::GetWindowRect
- AFXLAYOUT/CMFCDynamicLayout::HasItem
- AFXLAYOUT/CMFCDynamicLayout::IsEmpty
- AFXLAYOUT/CMFCDynamicLayout::LoadResource
- AFXLAYOUT/CMFCDynamicLayout::SetMinSize
dev_langs:
- C++
ms.assetid: c2df2976-f049-47fc-9cf0-abe3e01948bc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6604ada6dc4d322011a835c03731f6a48be472f2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcdynamiclayout-class"></a>CMFCDynamicLayout 類別
指定使用者調整視窗大小時，控制項在視窗中如何移動和調整大小。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCDynamicLayout : public CObject  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|`CMFCDynamicLayout::CMFCDynamicLayout`|建構 `CMFCDynamicLayout` 物件。|  
|`CMFCDynamicLayout::~CMFCDynamicLayout`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[Cmfcdynamiclayout:: Additem](#additem)|將子視窗 (通常是控制項) 加入至動態配置管理員所控制的視窗清單。|  
|[Cmfcdynamiclayout:: Adjust](#adjust)|將子視窗 (通常是控制項) 加入至動態配置管理員所控制的視窗清單。|  
|[CMFCDynamicLayout::Create](#create)|儲存並驗證主控視窗。|  
|[CMFCDynamicLayout::GetHostWnd](#gethostwnd)|傳回主控視窗的指標。|  
|[CMFCDynamicLayout::GetMinSize](#getminsize)|傳回視窗大小下限，低於此值就不調整版面配置。|  
|[CMFCDynamicLayout::GetWindowRect](#getwindowrect)|擷取視窗的目前用戶端區域的週框。|  
|[Cmfcdynamiclayout:: Hasitem](#hasitem)|檢查如果子控制項是否已加入動態配置。|  
|[Cmfcdynamiclayout:: Isempty](#isempty)|檢查動態配置是否未加入任何子視窗。|  
|[CMFCDynamicLayout::LoadResource](#loadresource)|從 AFX_DIALOG_LAYOUT 資源讀取動態配置，然後將配置套用至主控視窗。|  
|靜態[cmfcdynamiclayout:: Movehorizontal](#movehorizontal)|取得[MoveSettings](#movesettings_structure)定義當使用者調整其裝載視窗大小時，水平移動量子控制項的值。|  
|靜態[cmfcdynamiclayout:: Movehorizontalandvertical](#movehorizontalandvertical)|取得[MoveSettings](#movesettings_structure)定義當使用者調整其裝載視窗大小時，水平移動量子控制項的值。|  
|靜態[cmfcdynamiclayout:: Movenone](#movenone)|取得[MoveSettings](#movesettings_structure)值，表示垂直或水平，子控制項沒有移動。|  
|靜態[cmfcdynamiclayout:: Movevertical](#movevertical)|取得[MoveSettings](#movesettings_structure)定義當使用者調整其裝載視窗大小時，垂直移動量子控制項的值。|  
|[CMFCDynamicLayout::SetMinSize](#setminsize)|設定視窗大小下限，低於此值就不調整版面配置。|  
|靜態[cmfcdynamiclayout:: Sizehorizontal](#sizehorizontal)|取得[SizeSettings](#sizesettings_structure)定義當使用者調整其裝載視窗大小時，水平調整多少子控制項的值。|  
|靜態[cmfcdynamiclayout:: Sizehorizontalandvertical](#sizehorizontalandvertical)|取得[SizeSettings](#sizesettings_structure)定義當使用者調整其裝載視窗大小時，水平調整多少子控制項的值。|  
|靜態[cmfcdynamiclayout:: Sizenone](#sizenone)|取得[SizeSettings](#sizesettings_structure)值，表示子控制項的大小沒有變更。|  
|靜態[cmfcdynamiclayout:: Sizevertical](#sizevertical)|取得[SizeSettings](#sizesettings_structure)定義當使用者調整其裝載視窗大小時，垂直調整多少子控制項的值。|  
  
## <a name="nested-types"></a>巢狀類型  
  
|名稱|描述|  
|----------|-----------------|  
|[Cmfcdynamiclayout:: Movesettings 結構](#movesettings_structure)|為動態配置中控制項封裝移動資料。|  
|[Cmfcdynamiclayout:: Sizesettings 結構](#sizesettings_structure)|為動態配置中的控制項封裝大小變更資料。|  
  
## <a name="remarks"></a>備註  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCDynamicLayout](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxlayout.h  
  
##  <a name="additem"></a>Cmfcdynamiclayout:: Additem  
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
  
##  <a name="adjust"></a>Cmfcdynamiclayout:: Adjust  
 將子視窗 (通常是控制項) 加入至動態配置管理員所控制的視窗清單。  
  
```  
void Adjust();
```  
  
### <a name="remarks"></a>備註  
 調整主控視窗的大小時，子控制項的位置和大小會動態變更。  
  
##  <a name="create"></a>CMFCDynamicLayout::Create  
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
  
##  <a name="gethostwnd"></a>CMFCDynamicLayout::GetHostWnd  
 傳回主控視窗的指標。  
  
```  
CWnd* GetHostWnd();
```  
  
### <a name="return-value"></a>傳回值  
 主控視窗的指標。  
  
### <a name="remarks"></a>備註  
 根據預設，會重新計算所有子控制項相對於此視窗的位置。  
  
##  <a name="getminsize"></a>CMFCDynamicLayout::GetMinSize  
 傳回視窗大小下限，低於此值就不調整版面配置。  
  
```  
CSize GetMinSize();
```  
  
### <a name="return-value"></a>傳回值  
 視窗大小下限，低於此值就不調整版面配置。  
  
### <a name="remarks"></a>備註  
 調整主控視窗的大小時，子控制項的位置和大小會動態變更，但是有大小下限，低於此值就不會調整版面配置。 使用者可以將視窗調小，但視窗的某些部分就看不見。  
  
##  <a name="getwindowrect"></a>CMFCDynamicLayout::GetWindowRect  
 擷取視窗的目前用戶端區域的週框。  
  
```  
void GetHostWndRect(CRect& rect,);
```  
  
### <a name="parameters"></a>參數  
 `rect`  
 在此函數傳回之後，此參數會包含版面配置區域的週框。 這是輸出參數；輸入值會被覆寫。  
  
### <a name="remarks"></a>備註  
  
##  <a name="hasitem"></a>Cmfcdynamiclayout:: Hasitem  
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
  
##  <a name="isempty"></a>Cmfcdynamiclayout:: Isempty  
 檢查動態配置是否未加入任何子視窗。  
  
```  
BOOL IsEmpty();
```  
  
### <a name="return-value"></a>傳回值  
 如果配置沒有任何項目，則為 TRUE，否則為 FALSE。  
  
### <a name="remarks"></a>備註  
  
##  <a name="loadresource"></a>CMFCDynamicLayout::LoadResource  
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
  
##  <a name="movehorizontal"></a>Cmfcdynamiclayout:: Movehorizontal  
 取得[MoveSettings](#movesettings_structure)定義當使用者調整其裝載視窗大小時，水平移動量子控制項的值。  
  
```  
static MoveSettings MoveHorizontal(int nRatio);  
```  
  
### <a name="parameters"></a>參數  
 `nRatio`  
 定義當使用者調整主視窗大小時，水平移動子控制項的幅度百分比。  
  
### <a name="return-value"></a>傳回值  
 A [MoveSettings](#movesettings_structure)封裝要求的值的移動比率。  
  
### <a name="remarks"></a>備註  
  
##  <a name="movehorizontalandvertical"></a>Cmfcdynamiclayout:: Movehorizontalandvertical  
 取得[MoveSettings](#movesettings_structure)定義當使用者調整其裝載視窗大小時，水平移動量子控制項的值。  
  
```  
static MoveSettings MoveHorizontalAndVertical(int nXRatio int nYRatio);  
```  
  
### <a name="parameters"></a>參數  
 `nXRatio`  
 定義當使用者調整主視窗大小時，水平移動子控制項的幅度百分比。  
  
 `nYRatio`  
 定義當使用者調整主視窗大小時，垂直移動子控制項的幅度百分比。  
  
### <a name="return-value"></a>傳回值  
 A [MoveSettings](#movesettings_structure)封裝要求的值的移動比率。  
  
### <a name="remarks"></a>備註  
  
##  <a name="movenone"></a>Cmfcdynamiclayout:: Movenone  
 取得[MoveSettings](#movesettings_structure)值，表示垂直或水平，子控制項沒有移動。  
  
```  
static MoveSettings MoveNone();  
```  
  
### <a name="return-value"></a>傳回值  
 A [MoveSettings](#movesettings_structure)修正控制項的位置，讓它不會移動隨著使用者調整主控視窗的值。  
  
### <a name="remarks"></a>備註  
  
##  <a name="movesettings_structure"></a>Cmfcdynamiclayout:: Movesettings 結構  
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

##  <a name="movevertical"></a>Cmfcdynamiclayout:: Movevertical  
 取得[MoveSettings](#movesettings_structure)定義當使用者調整其裝載視窗大小時，垂直移動量子控制項的值。  
  
```  
static MoveSettings MoveVertical(int nRatio);  
```  
  
### <a name="parameters"></a>參數  
 `nRatio`  
 定義當使用者調整主視窗大小時，垂直移動子控制項的幅度百分比。  
  
### <a name="return-value"></a>傳回值  
 A [MoveSettings](#movesettings_structure)封裝要求的值的移動比率。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setminsize"></a>CMFCDynamicLayout::SetMinSize  
 設定視窗大小下限，低於此值就不調整版面配置。  
  
```  
void SetMinSize(const CSize& size);
```  
  
### <a name="parameters"></a>參數  
 `size`  
 所需的大小下限，低於此值就不調整版面配置。  
  
### <a name="remarks"></a>備註  
 調整主控視窗的大小時，子控制項的位置和大小會動態變更，但是有大小下限，低於此值就不會調整版面配置。 使用者可以將視窗調小，但視窗的某些部分就看不見。  
  
##  <a name="sizehorizontal"></a>Cmfcdynamiclayout:: Sizehorizontal  
 取得[SizeSettings](#sizesettings_structure)定義當使用者調整其裝載視窗大小時，水平調整多少子控制項的值。  
  
```  
static SizeSettings SizeHorizontal(int nRatio);  
```  
  
### <a name="parameters"></a>參數  
 `nRatio`  
 定義當使用者調整主視窗大小時，水平調整子控制項大小的幅度百分比。  
  
### <a name="return-value"></a>傳回值  
 A [SizeSettings](#sizesettings_structure)封裝要求的大小比率的值。  
  
### <a name="remarks"></a>備註  
  
##  <a name="sizehorizontalandvertical"></a>Cmfcdynamiclayout:: Sizehorizontalandvertical  
 取得[SizeSettings](#sizesettings_structure)定義當使用者調整其裝載視窗大小時，水平調整多少子控制項的值。  
  
```  
static SizeSettings SizeHorizontalAndVertical(int nXRatio int nYRatio);  
```  
  
### <a name="parameters"></a>參數  
 `nXRatio`  
 定義當使用者調整主視窗大小時，水平調整子控制項大小的幅度百分比。  
  
 `nYRatio`  
 定義當使用者調整主視窗大小時，垂直調整子控制項大小的幅度百分比。  
  
### <a name="return-value"></a>傳回值  
 A [SizeSettings](#sizesettings_structure)封裝要求的大小比率的值。  
  
### <a name="remarks"></a>備註  
  
##  <a name="sizenone"></a>Cmfcdynamiclayout:: Sizenone  
 取得[SizeSettings](#sizesettings_structure)值，表示子控制項的大小沒有變更。  
  
```  
static SizeSettings SizeNone();  
```  
  
### <a name="return-value"></a>傳回值  
 A [SizeSettings](#sizesettings_structure)控制項修正特定大小，讓它不會變更大小，隨著使用者調整主控視窗的值。  
  
### <a name="remarks"></a>備註  
  
##  <a name="sizesettings_structure"></a>Cmfcdynamiclayout:: Sizesettings 結構  
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

##  <a name="sizevertical"></a>Cmfcdynamiclayout:: Sizevertical  
 取得[SizeSettings](#sizesettings_structure)定義當使用者調整其裝載視窗大小時，垂直調整多少子控制項的值。  
  
```  
static SizeSettings SizeVertical(int nRatio);  
```  
  
### <a name="parameters"></a>參數  
 `nRatio`  
 定義當使用者調整主視窗大小時，垂直調整子控制項大小的幅度百分比。  
  
### <a name="return-value"></a>傳回值  
 A [SizeSettings](#sizesettings_structure)封裝要求的大小比率的值。  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)

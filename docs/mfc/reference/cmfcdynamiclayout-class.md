---
title: CMFCDynamicLayout 類別
ms.date: 08/29/2019
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
ms.assetid: c2df2976-f049-47fc-9cf0-abe3e01948bc
ms.openlocfilehash: 77dd3a84a0c76b92495bb062eeb83ff013933087
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752384"
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
|[CMFCDynamicLayout::AddItem](#additem)|將子視窗 (通常是控制項) 加入至動態配置管理員所控制的視窗清單。|
|[CMFCDynamicLayout::Adjust](#adjust)|將子視窗 (通常是控制項) 加入至動態配置管理員所控制的視窗清單。|
|[CMFCDynamicLayout::Create](#create)|儲存並驗證主控視窗。|
|[CMFCDynamicLayout::GetHostWnd](#gethostwnd)|傳回主控視窗的指標。|
|[CMFCDynamicLayout::GetMinSize](#getminsize)|傳回視窗大小下限，低於此值就不調整版面配置。|
|[CMFCDynamicLayout::GetWindowRect](#getwindowrect)|擷取視窗的目前用戶端區域的週框。|
|[CMFCDynamicLayout::HasItem](#hasitem)|檢查如果子控制項是否已加入動態配置。|
|[CMFCDynamicLayout::IsEmpty](#isempty)|檢查動態配置是否未加入任何子視窗。|
|[CMFCDynamicLayout::LoadResource](#loadresource)|從 AFX_DIALOG_LAYOUT 資源讀取動態配置，然後將配置套用至主控視窗。|
|靜態[CMFC 動態佈局::移動水準](#movehorizontal)|獲取[MoveSettings](#movesettings_structure)值,該值定義使用者調整其託管視窗的大小時,子控件的水準移動量。|
|靜態[CMFC 動態佈局::移動水準和垂直](#movehorizontalandvertical)|獲取[MoveSettings](#movesettings_structure)值,該值定義使用者調整其託管視窗的大小時,子控件的水準移動量。|
|靜態[CMFC 動態佈局::移動無](#movenone)|獲取表示子控制項沒有垂直或水平運動的[MoveSettings](#movesettings_structure)值。|
|靜態[CMFC 動態佈局::垂直移動](#movevertical)|獲取[MoveSettings](#movesettings_structure)值,該值定義使用者調整其託管視窗的大小時垂直移動子控制項的大小。|
|[CMFCDynamicLayout::SetMinSize](#setminsize)|設定視窗大小下限，低於此值就不調整版面配置。|
|靜態[CMFC 動態佈局::水準大小](#sizehorizontal)|獲取[SizeSettings](#sizesettings_structure)值,該值定義當用戶調整其宿主視窗的大小時,子控制件水準調整大小的大小。|
|靜態[CMFC 動態佈局::水平和垂直大小](#sizehorizontalandvertical)|獲取[SizeSettings](#sizesettings_structure)值,該值定義當用戶調整其宿主視窗的大小時,子控制件水準調整大小的大小。|
|靜態[CMFC 動態佈局::大小無](#sizenone)|獲取表示子控制件大小不更改的[SizeSettings](#sizesettings_structure)值。|
|靜態[CMFC 動態佈局:: 垂直尺寸](#sizevertical)|獲取[SizeSettings](#sizesettings_structure)值,該值定義當用戶調整其宿主視窗的大小時垂直調整子控制件的大小。|

## <a name="nested-types"></a>巢狀類型

|名稱|描述|
|----------|-----------------|
|[CMFCDynamicLayout::MoveSettings 結構](#movesettings_structure)|為動態配置中控制項封裝移動資料。|
|[CMFCDynamicLayout::SizeSettings 結構](#sizesettings_structure)|為動態配置中的控制項封裝大小變更資料。|

## <a name="remarks"></a>備註

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CMFCDynamicLayout](../../mfc/reference/cmfctoolbarbutton-class.md)

## <a name="requirements"></a>需求

**標題:** afxlayout.h

## <a name="cmfcdynamiclayoutadditem"></a><a name="additem"></a>CMFC動態佈局::添加專案

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

*霍恩德*<br/>
要加入之視窗的控制代碼。

*nID*<br/>
要加入之子控制項的 ID。

*移動設定*<br/>
說明在視窗大小變更時應如何移動控制項的結構。

*大小設定*<br/>
說明在視窗大小變更時應如何為控制項調整大小的結構。

### <a name="return-value"></a>傳回值

如果成功加入項目則為 True，否則為 False。

### <a name="remarks"></a>備註

調整主控視窗的大小時，子控制項的位置和大小會動態變更。

## <a name="cmfcdynamiclayoutadjust"></a><a name="adjust"></a>CMFC動態佈局:調整

將子視窗 (通常是控制項) 加入至動態配置管理員所控制的視窗清單。

```cpp
void Adjust();
```

### <a name="remarks"></a>備註

調整主控視窗的大小時，子控制項的位置和大小會動態變更。

## <a name="cmfcdynamiclayoutcreate"></a><a name="create"></a>CMFC動態佈局:建立

儲存並驗證主控視窗。

```
BOOL Create(CWnd* pHostWnd);
```

### <a name="parameters"></a>參數

*pHostWnd*<br/>
主控視窗的指標。

### <a name="return-value"></a>傳回值

如果作業成功，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

## <a name="cmfcdynamiclayoutgethostwnd"></a><a name="gethostwnd"></a>CMFC動態佈局::獲取主機

傳回主控視窗的指標。

```
CWnd* GetHostWnd();
```

### <a name="return-value"></a>傳回值

主控視窗的指標。

### <a name="remarks"></a>備註

根據預設，會重新計算所有子控制項相對於此視窗的位置。

## <a name="cmfcdynamiclayoutgetminsize"></a><a name="getminsize"></a>CMFC動態佈局:取得最小值

傳回視窗大小下限，低於此值就不調整版面配置。

```
CSize GetMinSize();
```

### <a name="return-value"></a>傳回值

視窗大小下限，低於此值就不調整版面配置。

### <a name="remarks"></a>備註

調整主控視窗的大小時，子控制項的位置和大小會動態變更，但是有大小下限，低於此值就不會調整版面配置。 使用者可以將視窗調小，但視窗的某些部分就看不見。

## <a name="cmfcdynamiclayoutgetwindowrect"></a><a name="getwindowrect"></a>CMFC動態佈局::取得視窗重新

擷取視窗的目前用戶端區域的週框。

```cpp
void GetHostWndRect(CRect& rect,);
```

### <a name="parameters"></a>參數

*矩形*<br/>
在此函數傳回之後，此參數會包含版面配置區域的週框。 這是輸出參數；輸入值會被覆寫。

### <a name="remarks"></a>備註

## <a name="cmfcdynamiclayouthasitem"></a><a name="hasitem"></a>CMFC動態佈局::有專案

檢查如果子控制項是否已加入動態配置。

```
BOOL HasItem(HWND hwnd);
```

### <a name="parameters"></a>參數

*霍恩德*<br/>
控制項的視窗控制代碼。

### <a name="return-value"></a>傳回值

如果配置已有此項目，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

## <a name="cmfcdynamiclayoutisempty"></a><a name="isempty"></a>CMFC動態佈局::空

檢查動態配置是否未加入任何子視窗。

```
BOOL IsEmpty();
```

### <a name="return-value"></a>傳回值

如果配置沒有任何項目，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

## <a name="cmfcdynamiclayoutloadresource"></a><a name="loadresource"></a>CMFC動態佈局::載入資源

從 AFX_DIALOG_LAYOUT 資源讀取動態配置，然後將配置套用至主控視窗。

```
static BOOL LoadResource(CWnd* pHostWnd,
    LPVOID lpResource,
    DWORD dwSize);
```

### <a name="parameters"></a>參數

*pHostWnd*<br/>
主控視窗的指標。

*lp資源*<br/>
包含 AFX_DIALOG_LAYOUT 資源的緩衝區的指標。

*dwSize*<br/>
緩衝區大小，以位元組為單位。

### <a name="return-value"></a>傳回值

如果載入資源並將其套用至主控視窗中，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

## <a name="cmfcdynamiclayoutmovehorizontal"></a><a name="movehorizontal"></a>CMFC 動態佈局::移動水準

獲取[MoveSettings](#movesettings_structure)值,該值定義使用者調整其託管視窗的大小時,子控件的水準移動量。

```
static MoveSettings MoveHorizontal(int nRatio);
```

### <a name="parameters"></a>參數

*nRatio*<br/>
定義當使用者調整主視窗大小時，水平移動子控制項的幅度百分比。

### <a name="return-value"></a>傳回值

封裝請求的移動比的[移動設置](#movesettings_structure)值。

### <a name="remarks"></a>備註

## <a name="cmfcdynamiclayoutmovehorizontalandvertical"></a><a name="movehorizontalandvertical"></a>CMFC動態佈局::移動水準和垂直

獲取[MoveSettings](#movesettings_structure)值,該值定義使用者調整其託管視窗的大小時,子控件的水準移動量。

```
static MoveSettings MoveHorizontalAndVertical(int nXRatio int nYRatio);
```

### <a name="parameters"></a>參數

*nXRatio*<br/>
定義當使用者調整主視窗大小時，水平移動子控制項的幅度百分比。

*nYRatio*<br/>
定義當使用者調整主視窗大小時，垂直移動子控制項的幅度百分比。

### <a name="return-value"></a>傳回值

封裝請求的移動比的[移動設置](#movesettings_structure)值。

### <a name="remarks"></a>備註

## <a name="cmfcdynamiclayoutmovenone"></a><a name="movenone"></a>CMFC動態佈局::移動無

獲取表示子控制項沒有垂直或水平運動的[MoveSettings](#movesettings_structure)值。

```
static MoveSettings MoveNone();
```

### <a name="return-value"></a>傳回值

一個[MoveSettings](#movesettings_structure)值,用於修復控制項,以便在使用者調整主機視窗大小時不會移動。

### <a name="remarks"></a>備註

## <a name="cmfcdynamiclayoutmovesettings-structure"></a><a name="movesettings_structure"></a>CMFC動態佈局::移動設置結構

為動態配置中控制項封裝移動資料。

```
struct CMFCDynamicLayout::MoveSettings;
```

### <a name="remarks"></a>備註

這是 `CMFCDynamicLayout` 內部的巢狀類別。

## <a name="cmfcdynamiclayoutmovesettingsishorizontal"></a>CMFC 動態佈局::移動設置::是水準的

檢查移動資料是否指定非零的水平移動。

```
BOOL IsHorizontal() const
```

## <a name="return-value"></a>傳回值

如果 `MoveSettings` 物件指定非零的水平移動，則為 TRUE。

## <a name="cmfcdynamiclayoutmovesettingsisnone"></a>CMFC動態佈局::移動設置::無

檢查移動資料是否指定不移動。

```
BOOL IsNone() const
```

## <a name="return-value"></a>傳回值

如果 `MoveSettings` 物件指定不移動，則為 TRUE 。

## <a name="cmfcdynamiclayoutmovesettingsisvertical"></a>CMFC 動態佈局::移動設置::垂直

請檢查移動資料是否指定非零的垂直移動。

```
BOOL IsVertical() const
```

## <a name="return-value"></a>傳回值

如果 `MoveSettings` 物件指定非零的垂直移動，則為 TRUE。

## <a name="cmfcdynamiclayoutmovevertical"></a><a name="movevertical"></a>CMFC動態佈局::垂直移動

獲取[MoveSettings](#movesettings_structure)值,該值定義使用者調整其託管視窗的大小時垂直移動子控制項的大小。

```
static MoveSettings MoveVertical(int nRatio);
```

### <a name="parameters"></a>參數

*nRatio*<br/>
定義當使用者調整主視窗大小時，垂直移動子控制項的幅度百分比。

### <a name="return-value"></a>傳回值

封裝請求的移動比的[移動設置](#movesettings_structure)值。

### <a name="remarks"></a>備註

## <a name="cmfcdynamiclayoutsetminsize"></a><a name="setminsize"></a>CMFC 動態佈局::設定最小值

設定視窗大小下限，低於此值就不調整版面配置。

```cpp
void SetMinSize(const CSize& size);
```

### <a name="parameters"></a>參數

*size*<br/>
所需的大小下限，低於此值就不調整版面配置。

### <a name="remarks"></a>備註

調整主控視窗的大小時，子控制項的位置和大小會動態變更，但是有大小下限，低於此值就不會調整版面配置。 使用者可以將視窗調小，但視窗的某些部分就看不見。

## <a name="cmfcdynamiclayoutsizehorizontal"></a><a name="sizehorizontal"></a>CMFC 動態佈局::水平大小

獲取[SizeSettings](#sizesettings_structure)值,該值定義當用戶調整其宿主視窗的大小時,子控制件水準調整大小的大小。

```
static SizeSettings SizeHorizontal(int nRatio);
```

### <a name="parameters"></a>參數

*nRatio*<br/>
定義當使用者調整主視窗大小時，水平調整子控制項大小的幅度百分比。

### <a name="return-value"></a>傳回值

封裝請求的大小比[的 SizeSettings](#sizesettings_structure)值。

### <a name="remarks"></a>備註

## <a name="cmfcdynamiclayoutsizehorizontalandvertical"></a><a name="sizehorizontalandvertical"></a>CMFC動態佈局::水平和垂直大小

獲取[SizeSettings](#sizesettings_structure)值,該值定義當用戶調整其宿主視窗的大小時,子控制件水準調整大小的大小。

```
static SizeSettings SizeHorizontalAndVertical(int nXRatio int nYRatio);
```

### <a name="parameters"></a>參數

*nXRatio*<br/>
定義當使用者調整主視窗大小時，水平調整子控制項大小的幅度百分比。

*nYRatio*<br/>
定義當使用者調整主視窗大小時，垂直調整子控制項大小的幅度百分比。

### <a name="return-value"></a>傳回值

封裝請求的大小比[的 SizeSettings](#sizesettings_structure)值。

### <a name="remarks"></a>備註

## <a name="cmfcdynamiclayoutsizenone"></a><a name="sizenone"></a>CMFC動態佈局::大小無

獲取表示子控制件大小不更改的[SizeSettings](#sizesettings_structure)值。

```
static SizeSettings SizeNone();
```

### <a name="return-value"></a>傳回值

[大小設置](#sizesettings_structure)值,用於將控制項固定在特定大小,以便它不會在使用者調整主機視窗大小時更改大小。

### <a name="remarks"></a>備註

## <a name="cmfcdynamiclayoutsizesettings-structure"></a><a name="sizesettings_structure"></a>CMFC動態佈局::大小設置結構

為動態配置中的控制項封裝大小變更資料。

```
struct CMFCDynamicLayout::SizeSettings;
```

### <a name="remarks"></a>備註

這是 `CMFCDynamicLayout` 內部的巢狀類別。

## <a name="cmfcdynamiclayoutsizesettingsishorizontal"></a>CMFC 動態佈局::大小設置::是水準的

檢查調整大小資料是否指定非零的水平調整大小。

```
BOOL IsHorizontal() const
```

## <a name="return-value"></a>傳回值

如果 `SizeSettings` 物件指定非零的水平調整大小，則為 TRUE。

## <a name="cmfcdynamiclayoutsizesettingsisnone"></a>CMFC動態佈局::大小設置::無

檢查調整大小資料是否指定不調整大小。

```
BOOL IsNone() const
```

## <a name="return-value"></a>傳回值

如果 `SizeSettings` 物件指定不調整大小，則為 TRUE 。

## <a name="cmfcdynamiclayoutsizesettingsisvertical"></a>CMFC 動態佈局::大小設置::垂直

檢查調整大小資料是否指定非零的垂直調整大小。

```
BOOL IsVertical() const
```

## <a name="return-value"></a>傳回值

如果 `SizeSettings` 物件指定非零的垂直調整大小，則為 TRUE。

## <a name="cmfcdynamiclayoutsizevertical"></a><a name="sizevertical"></a>CMFC 動態佈局:: 垂直尺寸

獲取[SizeSettings](#sizesettings_structure)值,該值定義當用戶調整其宿主視窗的大小時垂直調整子控制件的大小。

```
static SizeSettings SizeVertical(int nRatio);
```

### <a name="parameters"></a>參數

*nRatio*<br/>
定義當使用者調整主視窗大小時，垂直調整子控制項大小的幅度百分比。

### <a name="return-value"></a>傳回值

封裝請求的大小比[的 SizeSettings](#sizesettings_structure)值。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)

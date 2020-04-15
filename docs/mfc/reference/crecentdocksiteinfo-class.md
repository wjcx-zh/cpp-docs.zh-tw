---
title: CRecentDockSiteInfo 類別
ms.date: 11/04/2016
f1_keywords:
- CRecentDockSiteInfo
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::CleanUp
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::GetRecentDefaultPaneDivider
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::GetRecentDockedPercent
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::GetRecentDockedRect
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::GetRecentListOfPanes
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::GetRecentPaneContainer
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::GetRecentTabContainer
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::Init
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::IsRecentLeftPane
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::SaveListOfRecentPanes
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::SetInfo
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::StoreDockInfo
helpviewer_keywords:
- CRecentDockSiteInfo [MFC], CleanUp
- CRecentDockSiteInfo [MFC], GetRecentDefaultPaneDivider
- CRecentDockSiteInfo [MFC], GetRecentDockedPercent
- CRecentDockSiteInfo [MFC], GetRecentDockedRect
- CRecentDockSiteInfo [MFC], GetRecentListOfPanes
- CRecentDockSiteInfo [MFC], GetRecentPaneContainer
- CRecentDockSiteInfo [MFC], GetRecentTabContainer
- CRecentDockSiteInfo [MFC], Init
- CRecentDockSiteInfo [MFC], IsRecentLeftPane
- CRecentDockSiteInfo [MFC], SaveListOfRecentPanes
- CRecentDockSiteInfo [MFC], SetInfo
- CRecentDockSiteInfo [MFC], StoreDockInfo
ms.assetid: 2dd14f95-d5a2-4461-a7a5-2c6c36a3a165
ms.openlocfilehash: d2178881ea18f9dc5300bde838b01a516e6bb395
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370922"
---
# <a name="crecentdocksiteinfo-class"></a>CRecentDockSiteInfo 類別

該`CRecentDockSiteInfo`類是一個説明類,用於存儲[CPane 類](../../mfc/reference/cpane-class.md)的最近狀態資訊。

## <a name="syntax"></a>語法

```
class CRecentDockSiteInfo : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|`CRecentDockSiteInfo::CRecentDockSiteInfo`|預設建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CRecentDockSiteInfo::CleanUp](#cleanup)||
|[CRecentDockSiteInfo::GetRecentDefaultPaneDivider](#getrecentdefaultpanedivider)||
|[CRecentDockSiteInfo::GetRecentDockedPercent](#getrecentdockedpercent)||
|[CRecentDockSiteInfo::GetRecentDockedRect](#getrecentdockedrect)||
|[CRecentDockSiteInfo::GetRecentListOfPanes](#getrecentlistofpanes)||
|[CRecentDockSiteInfo::GetRecentPaneContainer](#getrecentpanecontainer)||
|[CRecentDockSiteInfo::GetRecentTabContainer](#getrecenttabcontainer)||
|[CRecentDockSiteInfo::Init](#init)||
|[CRecentDockSiteInfo::IsRecentLeftPane](#isrecentleftpane)||
|[CSsDockSite資訊::操作員 |](#operator_eq)||
|[CRecentDockSiteInfo::SaveListOfRecentPanes](#savelistofrecentpanes)||
|[CRecentDockSiteInfo::SetInfo](#setinfo)||
|[CRecentDockSiteInfo::StoreDockInfo](#storedockinfo)||

## <a name="remarks"></a>備註

`CRecentDockSiteInfo` 類別是資料管理類別。 它會追蹤 `CPane` 在停駐和浮動之間轉換時的最後狀態。 當使用者按兩下浮動可停駐窗格時，它會變成停駐。 按兩下停駐窗格會使其返回至先前的位置、大小及狀態。 同樣地，重新停駐窗格時，它會返回至其先前的停駐位置。 這個資料類別可以使其成行。 由於此類別的成員會儲存停駐窗格的狀態資訊，所以它們不應該由您的應用程式直接修改。

每次建立窗格式就會建立 `CRecentDockSiteInfo` 物件。 每個`CPane`物件都有一個成員變數[CPane:m_recentDockInfo,](../../mfc/reference/cpane-class.md#m_recentdockinfo)用於存儲此資訊。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CRecentDockSiteInfo](../../mfc/reference/crecentdocksiteinfo-class.md)

## <a name="requirements"></a>需求

**標題:** afxssdockSiteInfo.h

## <a name="crecentdocksiteinfocleanup"></a><a name="cleanup"></a>CSsdock網站資訊::清理

```
void CleanUp();
```

### <a name="remarks"></a>備註

## <a name="crecentdocksiteinfocrecentdocksiteinfo"></a><a name="crecentdocksiteinfo"></a>CSsDock網站資訊::C_ssdock網站資訊

```
CRecentDockSiteInfo(CPane* pBar);
```

### <a name="parameters"></a>參數

[在]*pBar*<br/>

### <a name="remarks"></a>備註

## <a name="crecentdocksiteinfogetrecentdefaultpanedivider"></a><a name="getrecentdefaultpanedivider"></a>CSsDock 網站資訊::取得最新預設窗格分隔器

```
CPaneDivider* GetRecentDefaultPaneDivider();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="crecentdocksiteinfogetrecentdockedpercent"></a><a name="getrecentdockedpercent"></a>CSsDockSite資訊::獲取最新停靠百分比

```
int GetRecentDockedPercent(BOOL bForSlider);
```

### <a name="parameters"></a>參數

[在]*bForSlider*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="crecentdocksiteinfogetrecentdockedrect"></a><a name="getrecentdockedrect"></a>CSsDockSite資訊::取得最新多克

```
CRect& GetRecentDockedRect(BOOL bForSlider);
```

### <a name="parameters"></a>參數

[在]*bForSlider*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="crecentdocksiteinfogetrecentlistofpanes"></a><a name="getrecentlistofpanes"></a>CSsdock 網站資訊::取得最新清單的窗格

```
CList<HWND, HWND>& GetRecentListOfPanes(BOOL bForSlider);
```

### <a name="parameters"></a>參數

[在]*bForSlider*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="crecentdocksiteinfogetrecentpanecontainer"></a><a name="getrecentpanecontainer"></a>CSsDockSite資訊::取得最新窗格容器

```
CPaneContainer* GetRecentPaneContainer(BOOL bForSlider);
```

### <a name="parameters"></a>參數

[在]*bForSlider*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="crecentdocksiteinfogetrecenttabcontainer"></a><a name="getrecenttabcontainer"></a>CSsdockSite資訊::取得最新選項卡容器

```
CPaneContainer* GetRecentTabContainer(BOOL bForSlider);
```

### <a name="parameters"></a>參數

[在]*bForSlider*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="crecentdocksiteinfoinit"></a><a name="init"></a>CSinDockSite資訊::Init

```
void Init();
```

### <a name="remarks"></a>備註

## <a name="crecentdocksiteinfoisrecentleftpane"></a><a name="isrecentleftpane"></a>CSsdocksite資訊::最近左窗格

```
BOOL IsRecentLeftPane(BOOL bForSlider);
```

### <a name="parameters"></a>參數

[在]*bForSlider*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="crecentdocksiteinfooperator-"></a><a name="operator_eq"></a>CSsDockSite資訊::操作員 |

```
CRecentDockSiteInfo& operator=(CRecentDockSiteInfo& src);
```

### <a name="parameters"></a>參數

[在]*斯爾克*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="crecentdocksiteinfosavelistofrecentpanes"></a><a name="savelistofrecentpanes"></a>CS.DockSite資訊::儲存最近窗格清單

```
void SaveListOfRecentPanes(CList<HWND,
    HWND>& lstOrg,
    BOOL bForSlider);
```

### <a name="parameters"></a>參數

[在]*CList<HWND*<br/>
[在]*lstOrg*<br/>
[在]*bForSlider*<br/>

### <a name="remarks"></a>備註

## <a name="crecentdocksiteinfosetinfo"></a><a name="setinfo"></a>CSsDock網站資訊::SetInfo

```
virtual void SetInfo(
    BOOL bForSlider,
    CRecentDockSiteInfo& srcInfo);
```

### <a name="parameters"></a>參數

[在]*bForSlider*<br/>
[在]*srcInfo*<br/>

### <a name="remarks"></a>備註

## <a name="crecentdocksiteinfostoredockinfo"></a><a name="storedockinfo"></a>CSsDock網站資訊::商店多克資訊

```
virtual void StoreDockInfo(
    CPaneContainer* pRecentContainer,
    CDockablePane* pTabbedBar = NULL);
```

### <a name="parameters"></a>參數

[在]*p 最新容器*<br/>
[在]*pTabbedBar*<br/>

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CDockSite Class](../../mfc/reference/cdocksite-class.md)

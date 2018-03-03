---
title: "CRecentDockSiteInfo 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0d0c3869b2a290de348b7c93630907d0e0c7613d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="crecentdocksiteinfo-class"></a>CRecentDockSiteInfo 類別
`CRecentDockSiteInfo`類別會儲存最新狀態資訊的協助程式類別[CPane 類別](../../mfc/reference/cpane-class.md)。  
  
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
|[CRecentDockSiteInfo::operator =](#operator_eq)||  
|[CRecentDockSiteInfo::SaveListOfRecentPanes](#savelistofrecentpanes)||  
|[CRecentDockSiteInfo::SetInfo](#setinfo)||  
|[CRecentDockSiteInfo::StoreDockInfo](#storedockinfo)||  
  
## <a name="remarks"></a>備註  
 `CRecentDockSiteInfo` 類別是資料管理類別。 它會追蹤 `CPane` 在停駐和浮動之間轉換時的最後狀態。 當使用者按兩下浮動可停駐窗格時，它會變成停駐。 按兩下停駐窗格會使其返回至先前的位置、大小及狀態。 同樣地，重新停駐窗格時，它會返回至其先前的停駐位置。 這個資料類別可以使其成行。 由於此類別的成員會儲存停駐窗格的狀態資訊，所以它們不應該由您的應用程式直接修改。  
  
 每次建立窗格式就會建立 `CRecentDockSiteInfo` 物件。 每個`CPane`物件具有成員變數， [cpane:: M_recentdockinfo](../../mfc/reference/cpane-class.md#m_recentdockinfo)來儲存這項資訊。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CRecentDockSiteInfo](../../mfc/reference/crecentdocksiteinfo-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxrecentDockSiteInfo.h  
  
##  <a name="cleanup"></a>CRecentDockSiteInfo::CleanUp  

  
```  
void CleanUp();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="crecentdocksiteinfo"></a>CRecentDockSiteInfo::CRecentDockSiteInfo  

  
```  
CRecentDockSiteInfo(CPane* pBar);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pBar`  
  
### <a name="remarks"></a>備註  
  
##  <a name="getrecentdefaultpanedivider"></a>CRecentDockSiteInfo::GetRecentDefaultPaneDivider  

  
```  
CPaneDivider* GetRecentDefaultPaneDivider();
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="getrecentdockedpercent"></a>CRecentDockSiteInfo::GetRecentDockedPercent  

  
```  
int GetRecentDockedPercent(BOOL bForSlider);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bForSlider`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="getrecentdockedrect"></a>CRecentDockSiteInfo::GetRecentDockedRect  

  
```  
CRect& GetRecentDockedRect(BOOL bForSlider);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bForSlider`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="getrecentlistofpanes"></a>CRecentDockSiteInfo::GetRecentListOfPanes  

  
```  
CList<HWND, HWND>& GetRecentListOfPanes(BOOL bForSlider);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bForSlider`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="getrecentpanecontainer"></a>CRecentDockSiteInfo::GetRecentPaneContainer  

  
```  
CPaneContainer* GetRecentPaneContainer(BOOL bForSlider);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bForSlider`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="getrecenttabcontainer"></a>CRecentDockSiteInfo::GetRecentTabContainer  

  
```  
CPaneContainer* GetRecentTabContainer(BOOL bForSlider);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bForSlider`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="init"></a>CRecentDockSiteInfo::Init  

  
```  
void Init();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="isrecentleftpane"></a>CRecentDockSiteInfo::IsRecentLeftPane  

  
```  
BOOL IsRecentLeftPane(BOOL bForSlider);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bForSlider`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="operator_eq"></a>CRecentDockSiteInfo::operator =  

  
```  
CRecentDockSiteInfo& operator=(CRecentDockSiteInfo& src);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `src`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="savelistofrecentpanes"></a>CRecentDockSiteInfo::SaveListOfRecentPanes  

  
```  
void SaveListOfRecentPanes(CList<HWND,  
    HWND>& lstOrg,  
    BOOL bForSlider);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `CList<HWND`  
 [輸入] `lstOrg`  
 [輸入] `bForSlider`  
  
### <a name="remarks"></a>備註  
  
##  <a name="setinfo"></a>CRecentDockSiteInfo::SetInfo  

  
```  
virtual void SetInfo(
    BOOL bForSlider,  
    CRecentDockSiteInfo& srcInfo);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bForSlider`  
 [輸入] `srcInfo`  
  
### <a name="remarks"></a>備註  
  
##  <a name="storedockinfo"></a>CRecentDockSiteInfo::StoreDockInfo  

  
```  
virtual void StoreDockInfo(
    CPaneContainer* pRecentContainer,  
    CDockablePane* pTabbedBar = NULL);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pRecentContainer`  
 [輸入] `pTabbedBar`  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CDockSite 類別](../../mfc/reference/cdocksite-class.md)

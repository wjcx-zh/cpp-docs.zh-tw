---
title: "CMonthCalCtrl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMonthCalCtrl
dev_langs:
- C++
helpviewer_keywords:
- month calendar controls, CMonthCalCtrl class
- common controls, Internet Explorer 4.0
- CMonthCalCtrl class
- Internet Explorer 4.0 common controls
- month calendar controls
ms.assetid: a42f6bd6-ab5c-4335-82f8-839982fc64a2
caps.latest.revision: 23
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
ms.openlocfilehash: 96cefbeb7692a07088f596fe08fec2bf179b98bc
ms.lasthandoff: 02/24/2017

---
# <a name="cmonthcalctrl-class"></a>CMonthCalCtrl 類別
封裝月曆控制項的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CMonthCalCtrl : public CWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CMonthCalCtrl::CMonthCalCtrl](#cmonthcalctrl)|建構 `CMonthCalCtrl` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMonthCalCtrl::Create](#create)|建立月曆控制項並將它附加`CMonthCalCtrl`物件。|  
|[CMonthCalCtrl::GetCalendarBorder](#getcalendarborder)|擷取目前月曆控制項的框線寬度。|  
|[CMonthCalCtrl::GetCalendarCount](#getcalendarcount)|擷取目前的月份行事曆控制項中顯示的行事曆的數目。|  
|[CMonthCalCtrl::GetCalendarGridInfo](#getcalendargridinfo)|擷取目前月曆控制項的相關資訊。|  
|[CMonthCalCtrl::GetCalID](#getcalid)|擷取目前月曆控制項的行事曆識別項。|  
|[CMonthCalCtrl::GetColor](#getcolor)|取得指定區域的月曆控制項中的色彩。|  
|[CMonthCalCtrl::GetCurrentView](#getcurrentview)|擷取目前正在顯示由目前月曆控制項的檢視。|  
|[CMonthCalCtrl::GetCurSel](#getcursel)|以目前選取的日期會擷取系統時間。|  
|[CMonthCalCtrl::GetFirstDayOfWeek](#getfirstdayofweek)|取得要顯示在最左邊的資料行的行事曆週的第一天。|  
|[CMonthCalCtrl::GetMaxSelCount](#getmaxselcount)|擷取目前的最大數目的月曆控制項中可選取的天數。|  
|[CMonthCalCtrl::GetMaxTodayWidth](#getmaxtodaywidth)|擷取目前月曆控制項的 「 今日 」 字串的最大寬度。|  
|[CMonthCalCtrl::GetMinReqRect](#getminreqrect)|擷取月曆控制項中顯示一整個月所需的最小大小。|  
|[CMonthCalCtrl::GetMonthDelta](#getmonthdelta)|擷取月曆控制項的捲動速率。|  
|[CMonthCalCtrl::GetMonthRange](#getmonthrange)|擷取日期代表高、 低限制的月曆控制項的顯示資訊。|  
|[CMonthCalCtrl::GetRange](#getrange)|擷取月曆控制項中設定的目前最小和最大日期。|  
|[CMonthCalCtrl::GetSelRange](#getselrange)|擷取日期資訊，表示目前使用者所選取的日期範圍的上限和下限。|  
|[CMonthCalCtrl::GetToday](#gettoday)|擷取指定為 「 目前 」 的月曆控制項的日期的日期資訊。|  
|[CMonthCalCtrl::HitTest](#hittest)|判斷哪一個區段的月曆控制項是在螢幕上指定的點。|  
|[CMonthCalCtrl::IsCenturyView](#iscenturyview)|指出目前月曆控制項的目前檢視是否為世紀檢視。|  
|[CMonthCalCtrl::IsDecadeView](#isdecadeview)|指出目前月曆控制項的目前檢視是十年來檢視。|  
|[CMonthCalCtrl::IsMonthView](#ismonthview)|指出目前月曆控制項的目前檢視是 [月] 檢視。|  
|[CMonthCalCtrl::IsYearView](#isyearview)|指出目前月曆控制項的目前檢視是否為 [年] 檢視。|  
|[CMonthCalCtrl::SetCalendarBorder](#setcalendarborder)|設定目前的月份行事曆控制項的框線寬度。|  
|[CMonthCalCtrl::SetCalendarBorderDefault](#setcalendarborderdefault)|設定目前月曆控制項的框線的預設寬度。|  
|[CMonthCalCtrl::SetCalID](#setcalid)|設定目前月曆控制項的行事曆識別碼。|  
|[CMonthCalCtrl::SetCenturyView](#setcenturyview)|設定目前的月份行事曆控制，以顯示世紀檢視。|  
|[CMonthCalCtrl::SetColor](#setcolor)|設定月曆控制項的指定區域的色彩。|  
|[CMonthCalCtrl::SetCurrentView](#setcurrentview)|設定目前的月份行事曆控制，以顯示指定的檢視。|  
|[CMonthCalCtrl::SetCurSel](#setcursel)|設定月曆控制項的目前所選取的日期。|  
|[Cmonthcalctrl:: Setdaystate](#setdaystate)|設定日期的顯示月曆控制項中。|  
|[CMonthCalCtrl::SetDecadeView](#setdecadeview)|目前的月曆控制項到十年來檢視設定。|  
|[CMonthCalCtrl::SetFirstDayOfWeek](#setfirstdayofweek)|設定要顯示在行事曆的最左邊的資料行中的週間日。|  
|[CMonthCalCtrl::SetMaxSelCount](#setmaxselcount)|設定月曆控制項中可選取最大天數。|  
|[CMonthCalCtrl::SetMonthDelta](#setmonthdelta)|設定月曆控制項的捲動速率。|  
|[CMonthCalCtrl::SetMonthView](#setmonthview)|設定目前的月份行事曆控制，以顯示 [月] 檢視。|  
|[CMonthCalCtrl::SetRange](#setrange)|設定最小值和最大允許月曆控制項的日期。|  
|[CMonthCalCtrl::SetSelRange](#setselrange)|選取月份行事曆控制項設定指定的日期範圍內。|  
|[CMonthCalCtrl::SetToday](#settoday)|設定為目前日期的日曆控制項。|  
|[CMonthCalCtrl::SetYearView](#setyearview)|目前的月曆控制項設定年檢視。|  
|[CMonthCalCtrl::SizeMinReq](#sizeminreq)|重繪月曆控制項為其最小值和一個月的大小。|  
|[CMonthCalCtrl::SizeRectToMin](#sizerecttomin)|目前的月份行事曆控制項中，計算的最小矩形可以包含所有符合指定的矩形中的行事曆。|  
  
## <a name="remarks"></a>備註  
 月曆控制項提供使用者簡單的行事曆介面，使用者可以從中選取一個日期。 使用者可以變更顯示的︰  
  
-   向上捲動與轉送、 每月的月。  
  
-   按一下以顯示目前日期的今天文字 (如果**MCS_NOTODAY**樣式不是)。  
  
-   挑選一個月或一年的快顯功能表。  
  
 您可以自訂每月月曆控制項將各種樣式套用至物件，當您在建立時。 這些樣式中所述[月份行事曆控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760919)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 月曆控制項可以顯示多個月份，且可以指出特殊天 （例如假日） 的粗體日期。  
  
 如需有關使用月曆控制項的詳細資訊，請參閱[使用 CMonthCalCtrl](../../mfc/using-cmonthcalctrl.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CMonthCalCtrl`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxdtctl.h  
  
##  <a name="a-namecmonthcalctrla--cmonthcalctrlcmonthcalctrl"></a><a name="cmonthcalctrl"></a>CMonthCalCtrl::CMonthCalCtrl  
 建構 `CMonthCalCtrl` 物件。  
  
```  
CMonthCalCtrl();
```  
  
### <a name="remarks"></a>備註  
 您必須呼叫**建立**建構物件之後。  
  
##  <a name="a-namecreatea--cmonthcalctrlcreate"></a><a name="create"></a>CMonthCalCtrl::Create  
 建立月曆控制項並將它附加`CMonthCalCtrl`物件。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);

 
virtual BOOL Create(
    DWORD dwStyle,  
    const POINT& pt,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 `dwStyle`  
 指定套用至月曆控制項的視窗樣式的組合。 請參閱[月份行事曆控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760919)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]如需有關樣式。  
  
 `rect`  
 參考[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構。 包含月曆控制項的大小和位置。  
  
 `pt`  
 參考[點](http://msdn.microsoft.com/library/windows/desktop/dd162805)結構，辨識月曆控制項的位置。  
  
 `pParentWnd`  
 指標[CWnd](../../mfc/reference/cwnd-class.md)是月曆控制項的父視窗的物件。 它不得為**NULL**。  
  
 `nID`  
 指定月曆控制項的控制項 id。  
  
### <a name="return-value"></a>傳回值  
 如果初始化成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 建立一個月月曆控制項中的兩個步驟︰  
  
1.  呼叫[CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)建構`CMonthCalCtrl`物件。  
  
2.  呼叫此成員函式，建立月曆控制項並將它附加`CMonthCalCtrl`物件。  
  
 當您呼叫**建立**，通用控制項都已初始化。 版本**建立**您呼叫可讓您決定大小的方式︰  
  
-   若要自動調整一個月控制項的 MFC，呼叫會使用覆寫`pt`參數。  
  
-   若要自行調整控制項，呼叫會使用此函式的覆寫`rect`參數。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CMonthCalCtrl #&1;](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_1.cpp)]  
  
##  <a name="a-namegetcalendarbordera--cmonthcalctrlgetcalendarborder"></a><a name="getcalendarborder"></a>CMonthCalCtrl::GetCalendarBorder  
 擷取目前月曆控制項的框線寬度。  
  
```  
int GetCalendarBorder() const;  
```  
  
### <a name="return-value"></a>傳回值  
 控制項框線，單位為像素的寬度。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[MCM_GETCALENDARBORDER](http://msdn.microsoft.com/library/windows/desktop/bb760945)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetcalendarcounta--cmonthcalctrlgetcalendarcount"></a><a name="getcalendarcount"></a>CMonthCalCtrl::GetCalendarCount  
 擷取目前的月份行事曆控制項中顯示的行事曆的數目。  
  
```  
int GetCalendarCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 月曆控制項中目前顯示的行事曆的數目。 行事曆的允許的數目上限是 12。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[MCM_GETCALENDARCOUNT](http://msdn.microsoft.com/library/windows/desktop/bb760947)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetcalendargridinfoa--cmonthcalctrlgetcalendargridinfo"></a><a name="getcalendargridinfo"></a>CMonthCalCtrl::GetCalendarGridInfo  
 擷取目前月曆控制項的相關資訊。  
  
```  
BOOL GetCalendarGridInfo(PMCGRIDINFO pmcGridInfo) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[輸出] `pmcGridInfo`|指標[MCGRIDINFO](http://msdn.microsoft.com/library/windows/desktop/bb760925)接收目前月曆控制項的相關資訊的結構。 呼叫端會負責配置與初始化此結構。|  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[MCM_GETCALENDARGRIDINFO](http://msdn.microsoft.com/library/windows/desktop/bb760949)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數， `m_monthCalCtrl`，也就是用來以程式設計方式存取月曆控制項。 下一個範例中會使用此變數。  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s&#1;&9;](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例使用`GetCalendarGridInfo`方法來擷取目前月曆控制項所顯示的行事曆日期。  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s&#1;&3;](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_3.cpp)]  
  
##  <a name="a-namegetcalida--cmonthcalctrlgetcalid"></a><a name="getcalid"></a>CMonthCalCtrl::GetCalID  
 擷取目前月曆控制項的行事曆識別項。  
  
```  
CALID GetCalID() const;  
```  
  
### <a name="return-value"></a>傳回值  
 其中一個[行事曆識別碼](http://msdn.microsoft.com/library/windows/desktop/dd317732)常數。  
  
### <a name="remarks"></a>備註  
 行事曆識別碼代表特定地區的行事曆，例如西曆 （已當地語系化）、 日文或回曆行事曆。 您的應用程式可以使用具有不同的語言支援函式的行事曆識別項。  
  
 這個方法會傳送[MCM_GETCALID](http://msdn.microsoft.com/library/windows/desktop/bb760951)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetcolora--cmonthcalctrlgetcolor"></a><a name="getcolor"></a>CMonthCalCtrl::GetColor  
 每月區域的色彩月曆控制項所指定的擷取`nRegion`。  
  
```  
COLORREF GetColor(int nRegion) const;  
```  
  
### <a name="parameters"></a>參數  
 `nRegion`  
 月曆控制項擷取色彩區域。 如需值的清單，請參閱`nRegion`參數[SetColor](#setcolor)。  
  
### <a name="return-value"></a>傳回值  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值，指定的月曆控制項，部分與相關聯的色彩，如果成功。 否則，此成員函式會傳回-1。  
  
##  <a name="a-namegetcurrentviewa--cmonthcalctrlgetcurrentview"></a><a name="getcurrentview"></a>CMonthCalCtrl::GetCurrentView  
 擷取目前正在顯示由目前月曆控制項的檢視。  
  
```  
DWORD GetCurrentView() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前檢視中會以下列值之一︰  
  
|值|意義|  
|-----------|-------------|  
|`MCMV_MONTH`|每月 檢視|  
|`MCMV_YEAR`|每年的檢視|  
|`MCMV_DECADE`|十年來檢視|  
|`MCMV_CENTURY`|世紀檢視|  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[MCM_GETCURRENTVIEW](http://msdn.microsoft.com/library/windows/desktop/bb760955)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數， `m_monthCalCtrl`，也就是用來以程式設計方式存取月曆控制項。 下一個範例中會使用此變數。  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s&#1;&9;](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例報表檢視月份行事曆控制目前顯示。  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s&#1;&7;](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_4.cpp)]  
  
##  <a name="a-namegetcursela--cmonthcalctrlgetcursel"></a><a name="getcursel"></a>CMonthCalCtrl::GetCurSel  
 以目前選取的日期會擷取系統時間。  
  
```  
BOOL GetCurSel(COleDateTime& refDateTime) const;  BOOL GetCurSel(CTime& refDateTime) const;  
   
BOOL GetCurSel(LPSYSTEMTIME pDateTime) const;  
```  
  
### <a name="parameters"></a>參數  
 `refDateTime`  
 參考[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件或[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件。 接收的目前時間。  
  
 `pDateTime`  
 指標[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)結構，將會收到將目前選取的日期資訊。 這個參數必須是有效的位址，而且不能**NULL**。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零otherwize 0。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[MCM_GETCURSEL](http://msdn.microsoft.com/library/windows/desktop/bb760957)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
> [!NOTE]
>  如果此成員函式會失敗樣式**MCS_MULTISELECT**設定。  
  
 在 MFC 的實作`GetCurSel`，您可以指定`COleDateTime`使用量，`CTime`使用量，或`SYSTEMTIME`結構使用。  
  
##  <a name="a-namegetfirstdayofweeka--cmonthcalctrlgetfirstdayofweek"></a><a name="getfirstdayofweek"></a>CMonthCalCtrl::GetFirstDayOfWeek  
 取得要顯示在最左邊的資料行的行事曆週的第一天。  
  
```  
int GetFirstDayOfWeek(BOOL* pbLocal = NULL) const;  
```  
  
### <a name="parameters"></a>參數  
 *pbLocal*  
 指標**BOOL**值。 如果值為非零，控制項的設定不符合在控制台中的設定。  
  
### <a name="return-value"></a>傳回值  
 整數值，表示當週的第一天。 請參閱**備註**如需有關這些整數所代表的項目。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[MCM_GETFIRSTDAYOFWEEK](http://msdn.microsoft.com/library/windows/desktop/bb760958)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 一周天數，統稱為整數，如下所示。  
  
|值|一週天數|  
|-----------|---------------------|  
|0|星期一|  
|1|星期二|  
|2|星期三|  
|3|星期四|  
|4|星期五|  
|5|星期六|  
|6|星期日|  
  
### <a name="example"></a>範例  
  請參閱範例[CMonthCalCtrl::SetFirstDayOfWeek](#setfirstdayofweek)。  
  
##  <a name="a-namegetmaxselcounta--cmonthcalctrlgetmaxselcount"></a><a name="getmaxselcount"></a>CMonthCalCtrl::GetMaxSelCount  
 擷取目前的最大數目的月曆控制項中可選取的天數。  
  
```  
int GetMaxSelCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 整數值，表示控制項，您可以選取日期的總數。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[MCM_GETMAXSELCOUNT](http://msdn.microsoft.com/library/windows/desktop/bb760960)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 使用此成員函式對於有控制項**MCS_MULTISELECT**樣式集。  
  
### <a name="example"></a>範例  
  請參閱範例[CMonthCalCtrl::SetMaxSelCount](#setmaxselcount)。  
  
##  <a name="a-namegetmaxtodaywidtha--cmonthcalctrlgetmaxtodaywidth"></a><a name="getmaxtodaywidth"></a>CMonthCalCtrl::GetMaxTodayWidth  
 擷取目前月曆控制項的 「 今日 」 字串的最大寬度。  
  
```  
DWORD GetMaxTodayWidth() const;  
```  
  
### <a name="return-value"></a>傳回值  
 「 今日 」 字串中，單位為像素寬度。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數， `m_monthCalCtrl`，也就是用來以程式設計方式存取月曆控制項。 下一個範例中會使用此變數。  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s&#1;&9;](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例示範`GetMaxTodayWidth`方法。  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s&#1;&1;](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_5.cpp)]  
  
### <a name="remarks"></a>備註  
 使用者可以按一下 「 今日 」 字串中，將月曆控制項的底部會顯示傳回目前的日期。 此 「 今日 」 字串包含標籤文字與日期。  
  
 這個方法會傳送[MCM_GETMAXTODAYWIDTH](http://msdn.microsoft.com/library/windows/desktop/bb760962)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetminreqrecta--cmonthcalctrlgetminreqrect"></a><a name="getminreqrect"></a>CMonthCalCtrl::GetMinReqRect  
 擷取月曆控制項中顯示一整個月所需的最小大小。  
  
```  
BOOL GetMinReqRect(RECT* pRect) const;  
```  
  
### <a name="parameters"></a>參數  
 `pRect`  
 指標[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)將收到周框矩形資訊的結構。 這個參數必須是有效的位址，而且不能**NULL**。  
  
### <a name="return-value"></a>傳回值  
 如果成功，此成員函式會傳回非零和`lpRect`接收適用週框的資訊。 如果不成功，成員函式會傳回 0。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[MCM_GETMINREQRECT](http://msdn.microsoft.com/library/windows/desktop/bb760978)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetmonthdeltaa--cmonthcalctrlgetmonthdelta"></a><a name="getmonthdelta"></a>CMonthCalCtrl::GetMonthDelta  
 擷取月曆控制項的捲動速率。  
  
```  
int GetMonthDelta() const;  
```  
  
### <a name="return-value"></a>傳回值  
 月曆控制項的捲動速率。 捲動速率是當使用者一次按一下捲軸按鈕控制項，會移動其顯示的月數。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[MCM_GETMONTHDELTA](http://msdn.microsoft.com/library/windows/desktop/bb760980)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetmonthrangea--cmonthcalctrlgetmonthrange"></a><a name="getmonthrange"></a>CMonthCalCtrl::GetMonthRange  
 擷取日期代表高、 低限制的月曆控制項的顯示資訊。  
  
```  
int GetMonthRange(
    COleDateTime& refMinRange,  
    COleDateTime& refMaxRange,  
    DWORD dwFlags) const;  
  
int GetMonthRange(
    CTime& refMinRange,  
    CTime& refMaxRange,  
    DWORD dwFlags) const;  
  
int GetMonthRange(
    LPSYSTEMTIME pMinRange,  
    LPSYSTEMTIME pMaxRange,  
    DWORD dwFlags) const;  
```  
  
### <a name="parameters"></a>參數  
 `refMinRange`  
 參考[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)或[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件，其中包含允許的最小日期。  
  
 `refMaxRange`  
 參考`COleDateTime`或`CTime`物件，其中包含允許的最大日期。  
  
 `pMinRange`  
 指標[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)結構，其中包含最低範圍的結尾處的日期。  
  
 `pMaxRange`  
 指標`SYSTEMTIME`結構，其中包含的日期範圍的最高的結尾。  
  
 `dwFlags`  
 值，指定要擷取的範圍限制的範圍。 此值必須是下列其中一個項目。  
  
|值|意義|  
|-----------|-------------|  
|GMR_DAYSTATE|包含開頭與結尾的可見範圍完整顯示的月數。|  
|GMR_VISIBLE|包括完全顯示的月份。|  
  
### <a name="return-value"></a>傳回值  
 整數，表示合併兩個限制的範圍，幾個月，由`refMinRange`和`refMaxRange`中的第一個和第二個版本，或`pMinRange`和`pMaxRange`第三個版本中。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[MCM_GETMONTHRANGE](http://msdn.microsoft.com/library/windows/desktop/bb760981)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 在 MFC 的實作`GetMonthRange`，您可以指定`COleDateTime`使用量，`CTime`使用量，或`SYSTEMTIME`結構使用。  
  
### <a name="example"></a>範例  
  請參閱範例[cmonthcalctrl:: Setdaystate](#setdaystate)。  
  
##  <a name="a-namegetrangea--cmonthcalctrlgetrange"></a><a name="getrange"></a>CMonthCalCtrl::GetRange  
 擷取月曆控制項中設定的目前最小和最大日期。  
  
```  
DWORD GetRange(
    COleDateTime* pMinRange,  
    COleDateTime* pMaxRange) const;  
  
DWORD GetRange(
    CTime* pMinRange,  
    CTime* pMaxRange) const;  
  
DWORD GetRange(
    LPSYSTEMTIME pMinRange,  
    LPSYSTEMTIME pMaxRange) const;  
```  
  
### <a name="parameters"></a>參數  
 `pMinRange`  
 指標`COleDateTime`物件，`CTime`物件，或[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)結構，其中包含最低範圍的結尾處的日期。  
  
 `pMaxRange`  
 指標`COleDateTime`物件，`CTime`物件，或[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)結構，其中包含的日期範圍的最高的結尾。  
  
### <a name="return-value"></a>傳回值  
 A `DWORD` ，可以是零 （設定不受限制） 或指定的限制資訊的下列值的組合。  
  
|值|意義|  
|-----------|-------------|  
|GDTR_MAX|最大限制是設定的控制項。`pMaxRange`有效，且包含適用於日期資訊。|  
|GDTR_MIN|最小的限制是設定的控制項;`pMinRange`有效，且包含適用於日期資訊。|  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[MCM_GETRANGE](http://msdn.microsoft.com/library/windows/desktop/bb760983)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 在 MFC 的實作`GetRange`，您可以指定`COleDateTime`使用量，`CTime`使用量，或`SYSTEMTIME`結構使用。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CMonthCalCtrl #&2;](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_6.cpp)]  
  
##  <a name="a-namegetselrangea--cmonthcalctrlgetselrange"></a><a name="getselrange"></a>CMonthCalCtrl::GetSelRange  
 擷取日期資訊，表示目前使用者所選取的日期範圍的上限和下限。  
  
```  
BOOL GetSelRange(
    COleDateTime& refMinRange,  
    COleDateTime& refMaxRange) const;  
  
BOOL GetSelRange(
    CTime& refMinRange,  
    CTime& refMaxRange) const;  
  
BOOL GetSelRange(
    LPSYSTEMTIME pMinRange,  
    LPSYSTEMTIME pMaxRange) const;  
```  
  
### <a name="parameters"></a>參數  
 `refMinRange`  
 參考[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)或[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件，其中包含允許的最小日期。  
  
 `refMaxRange`  
 參考`COleDateTime`或`CTime`物件，其中包含允許的最大日期。  
  
 `pMinRange`  
 指標[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)結構，其中包含最低範圍的結尾處的日期。  
  
 `pMaxRange`  
 指標`SYSTEMTIME`結構，其中包含的日期範圍的最高的結尾。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[MCM_GETSELRANGE](http://msdn.microsoft.com/library/windows/desktop/bb760985)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 `GetSelRange`如果套用至月曆控制項不會使用，將會失敗**MCS_MULTISELECT**樣式。  
  
 在 MFC 的實作`GetSelRange`，您可以指定`COleDateTime`使用量，`CTime`使用量，或`SYSTEMTIME`結構使用。  
  
##  <a name="a-namegettodaya--cmonthcalctrlgettoday"></a><a name="gettoday"></a>CMonthCalCtrl::GetToday  
 擷取指定為 「 目前 」 的月曆控制項的日期的日期資訊。  
  
```  
BOOL GetToday(COleDateTime& refDateTime) const;  BOOL GetToday(COleDateTime& refDateTime) const;  
   
BOOL GetToday(LPSYSTEMTIME pDateTime) const;  
```  
  
### <a name="parameters"></a>參數  
 `refDateTime`  
 參考[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)或[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件，表示目前的日期。  
  
 `pDateTime`  
 指標[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)結構將會接收日期資訊。 這個參數必須是有效的位址，而且不能**NULL**。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[MCM_GETTODAY](http://msdn.microsoft.com/library/windows/desktop/bb760987)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 在 MFC 的實作`GetToday`，您可以指定`COleDateTime`使用量，`CTime`使用量，或`SYSTEMTIME`結構使用。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CMonthCalCtrl #&3;](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_7.cpp)]  
  
##  <a name="a-namehittesta--cmonthcalctrlhittest"></a><a name="hittest"></a>CMonthCalCtrl::HitTest  
 如果有任何項目，是位於指定位置，決定哪一個月曆控制項。  
  
```  
DWORD HitTest(PMCHITTESTINFO pMCHitTest);
```  
  
### <a name="parameters"></a>參數  
 *pMCHitTest*  
 指標[MCHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb760927)月曆控制項的結構，包含點擊測試點。  
  
### <a name="return-value"></a>傳回值  
 `DWORD` 值。 等於**uHit**成員**MCHITTESTINFO**結構。  
  
### <a name="remarks"></a>備註  
 `HitTest`使用**MCHITTESTINFO**結構，其中包含點擊測試的相關資訊。  
  
##  <a name="a-nameiscenturyviewa--cmonthcalctrliscenturyview"></a><a name="iscenturyview"></a>CMonthCalCtrl::IsCenturyView  
 指出目前月曆控制項的目前檢視是否為世紀檢視。  
  
```  
BOOL IsCenturyView() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `true`如果目前的檢視是世紀的檢視。否則， `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[MCM_GETCURRENTVIEW](http://msdn.microsoft.com/library/windows/desktop/bb760955)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 如果訊息傳回`MCMV_CENTURY`，這個方法會傳回`true`。  
  
##  <a name="a-nameisdecadeviewa--cmonthcalctrlisdecadeview"></a><a name="isdecadeview"></a>CMonthCalCtrl::IsDecadeView  
 指出目前月曆控制項的目前檢視是十年來檢視。  
  
```  
BOOL IsDecadeView() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `true`如果目前的檢視是十年的檢視。否則， `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[MCM_GETCURRENTVIEW](http://msdn.microsoft.com/library/windows/desktop/bb760955)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 如果訊息傳回`MCMV_DECADE`，這個方法會傳回`true`。  
  
##  <a name="a-nameismonthviewa--cmonthcalctrlismonthview"></a><a name="ismonthview"></a>CMonthCalCtrl::IsMonthView  
 指出目前月曆控制項的目前檢視是 [月] 檢視。  
  
```  
BOOL IsMonthView() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `true`如果目前的檢視是 [月] 檢視中。否則， `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[MCM_GETCURRENTVIEW](http://msdn.microsoft.com/library/windows/desktop/bb760955)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 如果訊息傳回`MCMV_MONTH`，這個方法會傳回`true`。  
  
##  <a name="a-nameisyearviewa--cmonthcalctrlisyearview"></a><a name="isyearview"></a>CMonthCalCtrl::IsYearView  
 指出目前月曆控制項的目前檢視是否為 [年] 檢視。  
  
```  
BOOL IsYearView() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `true`如果目前的檢視是 [年] 檢視中。否則， `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[MCM_GETCURRENTVIEW](http://msdn.microsoft.com/library/windows/desktop/bb760955)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 如果訊息傳回`MCMV_YEAR`，這個方法會傳回`true`。  
  
##  <a name="a-namesetcalendarbordera--cmonthcalctrlsetcalendarborder"></a><a name="setcalendarborder"></a>CMonthCalCtrl::SetCalendarBorder  
 設定目前的月份行事曆控制項的框線寬度。  
  
```  
void SetCalendarBorder(int cxyBorder);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `cxyBorder`|框線寬度，單位為像素。|  
  
### <a name="remarks"></a>備註  
 如果此方法成功，框線寬度設為`cxyBorder`參數。 否則，框線寬度會重設為預設值，指定目前[佈景主題](https://msdn.microsoft.com/library/windows/desktop/hh270423.aspx)，或如果主題不會使用零。  
  
 這個方法會傳送[MCM_SETCALENDARBORDER](http://msdn.microsoft.com/library/windows/desktop/bb760993)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數， `m_monthCalCtrl`，也就是用來以程式設計方式存取月曆控制項。 下一個範例中會使用此變數。  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s&#1;&9;](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例會設定框線寬度的月曆控制項加入八個像素為單位。 使用[CMonthCalCtrl::GetCalendarBorder](#getcalendarborder)方法來判斷這個方法是否成功。  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s&#1;&6;](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_8.cpp)]  
  
##  <a name="a-namesetcalendarborderdefaulta--cmonthcalctrlsetcalendarborderdefault"></a><a name="setcalendarborderdefault"></a>CMonthCalCtrl::SetCalendarBorderDefault  
 設定目前月曆控制項的框線的預設寬度。  
  
```  
void SetCalendarBorderDefault();
```  
  
### <a name="remarks"></a>備註  
 框線寬度設定為目前所指定的預設值[佈景主題](https://msdn.microsoft.com/library/windows/desktop/hh270423.aspx)，或如果不使用主題為零。  
  
 這個方法會傳送[MCM_SETCALENDARBORDER](http://msdn.microsoft.com/library/windows/desktop/bb760993)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetcalida--cmonthcalctrlsetcalid"></a><a name="setcalid"></a>CMonthCalCtrl::SetCalID  
 設定目前月曆控制項的行事曆識別碼。  
  
```  
BOOL SetCalID(CALID calid);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `calid`|其中一個[行事曆識別碼](http://msdn.microsoft.com/library/windows/desktop/dd317732)常數。|  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 行事曆識別碼指定特定地區的行事曆，例如西曆 （已當地語系化）、 日文或回曆行事曆。 使用`SetCalID`方法，以顯示所指定的行事曆`calid`參數，如果您的電腦上已安裝包含行事曆的地區設定。  
  
 這個方法會傳送[MCM_SETCALID](http://msdn.microsoft.com/library/windows/desktop/bb760995)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數， `m_monthCalCtrl`，也就是用來以程式設計方式存取月曆控制項。 下一個範例中會使用此變數。  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s&#1;&9;](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例會設定月曆控制項來顯示日本天紀元行事曆。 `SetCalID`方法在您的電腦上安裝該行事曆時，才會成功。  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s&#1;&4;](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_9.cpp)]  
  
##  <a name="a-namesetcenturyviewa--cmonthcalctrlsetcenturyview"></a><a name="setcenturyview"></a>CMonthCalCtrl::SetCenturyView  
 設定目前的月份行事曆控制，以顯示世紀檢視。  
  
```  
BOOL SetCenturyView();
```  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會使用[CMonthCalCtrl::SetCurrentView](#setcurrentview)方法，檢視設定為`MCMV_CENTURY`，代表世紀檢視。  
  
##  <a name="a-namesetcolora--cmonthcalctrlsetcolor"></a><a name="setcolor"></a>CMonthCalCtrl::SetColor  
 設定月曆控制項的指定區域的色彩。  
  
```  
COLORREF SetColor(
    int nRegion,  
    COLORREF ref);
```  
  
### <a name="parameters"></a>參數  
 `nRegion`  
 整數值，指定哪一個月的行事曆色彩以設定。 這個值可以是下列其中一個項目。  
  
|值|意義|  
|-----------|-------------|  
|MCSC_BACKGROUND|背景色彩顯示幾個月之間。|  
|MCSC_MONTHBK|顯示於月份中的背景色彩。|  
|MCSC_TEXT|用來顯示月份內文字的色彩。|  
|MCSC_TITLEBK|顯示於日曆標題中的背景色彩。|  
|MCSC_TITLETEXT|用來顯示日曆標題內文字的色彩。|  
|MCSC_TRAILINGTEXT|用來顯示標頭和結尾的一天的文字色彩。 標頭和結尾天數是從目前的行事曆會出現之前與之後月份的天數。|  
  
 `ref`  
 A **COLORREF**月曆控制項的指定部分的新色彩設定的值。  
  
### <a name="return-value"></a>傳回值  
 A **COLORREF**值，如果成功，表示月曆控制項的指定部分原來的色彩設定。 否則此訊息會傳回-1。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[MCM_SETCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760997)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CMonthCalCtrl #&4;](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_10.cpp)]  
  
##  <a name="a-namesetcurrentviewa--cmonthcalctrlsetcurrentview"></a><a name="setcurrentview"></a>CMonthCalCtrl::SetCurrentView  
 設定目前的月份行事曆控制，以顯示指定的檢視。  
  
```  
BOOL SetCurrentView(DWORD dwNewView);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `dwNewView`|每月、 每年、 十年以上或世紀檢視指定下列值之一。<br /><br /> MCMV_MONTH︰ 每月 檢視<br /><br /> MCMV_YEAR︰ 每年檢視<br /><br /> MCMV_DECADE︰ 十年來檢視<br /><br /> MCMV_CENTURY︰ 世紀檢視|  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[MCM_SETCURRENTVIEW](http://msdn.microsoft.com/library/windows/desktop/bb760998)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetcursela--cmonthcalctrlsetcursel"></a><a name="setcursel"></a>CMonthCalCtrl::SetCurSel  
 設定月曆控制項的目前所選取的日期。  
  
```  
BOOL SetCurSel(const COleDateTime& refDateTime);  
BOOL SetCurSel(const CTime& refDateTime);  
  BOOL SetCurSel(const LPSYSTEMTIME pDateTime);
```  
  
### <a name="parameters"></a>參數  
 `refDateTime`  
 參考[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)或[CTime](../../atl-mfc-shared/reference/ctime-class.md)指示目前選取月曆控制項物件。  
  
 `pDateTime`  
 指標[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)結構，其中包含要設定為目前的選取範圍的日期。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[MCM_SETCURSEL](http://msdn.microsoft.com/library/windows/desktop/bb761002)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 在 MFC 的實作`SetCurSel`，您可以指定`COleDateTime`使用量，`CTime`使用量，或`SYSTEMTIME`結構使用。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CMonthCalCtrl #&5;](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_11.cpp)]  
  
##  <a name="a-namesetdaystatea--cmonthcalctrlsetdaystate"></a><a name="setdaystate"></a>Cmonthcalctrl:: Setdaystate  
 設定日期的顯示月曆控制項中。  
  
```  
BOOL SetDayState(
    int nMonths,  
    LPMONTHDAYSTATE pStates);
```  
  
### <a name="parameters"></a>參數  
 *nMonths*  
 值，表示陣列中有多少項目，`pStates`指向。  
  
 `pStates`  
 指標[MONTHDAYSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760915)定義如何月曆控制項時，會顯示在繪製每一天的值陣列。 **MONTHDAYSTATE**資料類型是位元欄位，其中每個位元 (1 到 31) 代表一個月裡一天的狀態。 如果位元是開啟的，則對應的日期會以粗體顯示；否則就不會強調其顯示。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[MCM_SETDAYSTATE](http://msdn.microsoft.com/library/windows/desktop/bb761004)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CMonthCalCtrl #&6;](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_12.cpp)]  
  
##  <a name="a-namesetdecadeviewa--cmonthcalctrlsetdecadeview"></a><a name="setdecadeview"></a>CMonthCalCtrl::SetDecadeView  
 目前的月曆控制項到十年來檢視設定。  
  
```  
BOOL SetDecadeView();
```  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會使用[CMonthCalCtrl::SetCurrentView](#setcurrentview)方法，檢視設定為`MCMV_DECADE`，這代表十年來檢視。  
  
##  <a name="a-namesetfirstdayofweeka--cmonthcalctrlsetfirstdayofweek"></a><a name="setfirstdayofweek"></a>CMonthCalCtrl::SetFirstDayOfWeek  
 設定要顯示在行事曆的最左邊的資料行中的週間日。  
  
```  
BOOL SetFirstDayOfWeek(
    int iDay,  
    int* lpnOld = NULL);
```  
  
### <a name="parameters"></a>參數  
 *iDay*  
 整數值，表示哪一天是設定為一週的第一天。 此值必須是其中一個日期的數字。 請參閱[GetFirstDayOfWeek](#getfirstdayofweek)日數字的說明。  
  
 *lpnOld*  
 一組表示先前的當週的第一天的整數指標。  
  
### <a name="return-value"></a>傳回值  
 如果先前的第一天一週中的設定以外的值為非零**LOCALE_IFIRSTDAYOFWEEK**，這是一天中控制面板設定指示。 否則，此函數會傳回 0。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[MCM_SETFIRSTDAYOFWEEK](http://msdn.microsoft.com/library/windows/desktop/bb761006)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CMonthCalCtrl #&7;](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_13.cpp)]  
  
##  <a name="a-namesetmaxselcounta--cmonthcalctrlsetmaxselcount"></a><a name="setmaxselcount"></a>CMonthCalCtrl::SetMaxSelCount  
 設定月曆控制項中可選取最大天數。  
  
```  
BOOL SetMaxSelCount(int nMax);
```  
  
### <a name="parameters"></a>參數  
 `nMax`  
 將代表最大天數可選取的值。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[MCM_SETMAXSELCOUNT](http://msdn.microsoft.com/library/windows/desktop/bb761008)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CMonthCalCtrl #&8;](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_14.cpp)]  
  
##  <a name="a-namesetmonthdeltaa--cmonthcalctrlsetmonthdelta"></a><a name="setmonthdelta"></a>CMonthCalCtrl::SetMonthDelta  
 設定月曆控制項的捲動速率。  
  
```  
int SetMonthDelta(int iDelta);
```  
  
### <a name="parameters"></a>參數  
 *iDelta*  
 要設定為控制項的捲動速率的月數。 如果此值為零，月份差異會重設為預設值是在控制項中顯示的月份數。  
  
### <a name="return-value"></a>傳回值  
 先前的捲動速率。 如果之前尚未設定的捲動速率，則傳回值為 0。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[MCM_SETMONTHDELTA](http://msdn.microsoft.com/library/windows/desktop/bb761010)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetmonthviewa--cmonthcalctrlsetmonthview"></a><a name="setmonthview"></a>CMonthCalCtrl::SetMonthView  
 設定目前的月份行事曆控制，以顯示 [月] 檢視。  
  
```  
BOOL SetMonthView();
```  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會使用[CMonthCalCtrl::SetCurrentView](#setcurrentview)方法，檢視設定為`MCMV_MONTH`，用來表示 [月] 檢視。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數， `m_monthCalCtrl`，也就是用來以程式設計方式存取月曆控制項。 下一個範例中會使用此變數。  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s&#1;&9;](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例會設定月曆控制項來顯示每月、 年、 十年來和世紀檢視。  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s&#1;&2;](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_15.cpp)]  
  
##  <a name="a-namesetrangea--cmonthcalctrlsetrange"></a><a name="setrange"></a>CMonthCalCtrl::SetRange  
 設定月曆控制項的最小和最大可允許日期。  
  
```  
BOOL SetRange(
    const COleDateTime* pMinRange,  
    const COleDateTime* pMaxRange);

 
BOOL SetRange(
    const CTime* pMinRange,  
    const CTime* pMaxRange);

 
BOOL SetRange(
    const LPSYSTEMTIME pMinRange,  
    const LPSYSTEMTIME pMaxRange);
```  
  
### <a name="parameters"></a>參數  
 `pMinRange`  
 指標`COleDateTime`物件，`CTime`物件，或[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)結構，其中包含最低範圍的結尾處的日期。  
  
 `pMaxRange`  
 指標`COleDateTime`物件，`CTime`物件，或`SYSTEMTIME`結構，其中包含的日期範圍的最高的結尾。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[MCM_SETRANGE](http://msdn.microsoft.com/library/windows/desktop/bb761012)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 在 MFC 的實作`SetRange`，您可以指定`COleDateTime`使用量，`CTime`使用量，或`SYSTEMTIME`結構使用。  
  
### <a name="example"></a>範例  
  請參閱範例[CMonthCalCtrl::GetRange](#getrange)。  
  
##  <a name="a-namesetselrangea--cmonthcalctrlsetselrange"></a><a name="setselrange"></a>CMonthCalCtrl::SetSelRange  
 選取月份行事曆控制項設定指定的日期範圍內。  
  
```  
BOOL SetSelRange(
    const COleDateTime& pMinRange,  
    const COleDateTime& pMaxRange);

 
BOOL SetSelRange(
    const CTime& pMinRange,  
    const CTime& pMaxRange);

 
BOOL SetSelRange(
    const LPSYSTEMTIME pMinRange,  
    const LPSYSTEMTIME pMaxRange);
```  
  
### <a name="parameters"></a>參數  
 `pMinRange`  
 指標`COleDateTime`物件，`CTime`物件，或[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)結構，其中包含最低範圍的結尾處的日期。  
  
 `pMaxRange`  
 指標`COleDateTime`物件，`CTime`物件，或`SYSTEMTIME`結構，其中包含的日期範圍的最高的結尾。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[MCM_SETSELRANGE](http://msdn.microsoft.com/library/windows/desktop/bb761014)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 在 MFC 的實作`SetSelRange`，您可以指定`COleDateTime`使用量，`CTime`使用量，或`SYSTEMTIME`結構使用。  
  
##  <a name="a-namesettodaya--cmonthcalctrlsettoday"></a><a name="settoday"></a>CMonthCalCtrl::SetToday  
 設定為目前日期的日曆控制項。  
  
```  
void SetToday(const COleDateTime& refDateTime);  
void SetToday(const CTime* pDateTime);  
  void SetToday(const LPSYSTEMTIME pDateTime);
```  
  
### <a name="parameters"></a>參數  
 `refDateTime`  
 參考[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件，其中包含目前的日期。  
  
 `pDateTime`  
 在第二個版本中，指標[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件，其中包含目前的日期資訊。 在第三個版本中，指標[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)結構，其中包含目前的日期資訊。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[MCM_SETTODAY](http://msdn.microsoft.com/library/windows/desktop/bb761016)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[CMonthCalCtrl::GetToday](#gettoday)。  
  
##  <a name="a-namesetyearviewa--cmonthcalctrlsetyearview"></a><a name="setyearview"></a>CMonthCalCtrl::SetYearView  
 目前的月曆控制項設定年檢視。  
  
```  
BOOL SetYearView();
```  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會使用[CMonthCalCtrl::SetCurrentView](#setcurrentview)方法，檢視設定為`MCMV_YEAR`，用來表示每年的檢視。  
  
##  <a name="a-namesizeminreqa--cmonthcalctrlsizeminreq"></a><a name="sizeminreq"></a>CMonthCalCtrl::SizeMinReq  
 顯示月曆控制項的最小大小的月份會顯示一個月。  
  
```  
BOOL SizeMinReq(BOOL bRepaint = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `bRepaint`  
 指定是否重新繪製控制項。 根據預設， **TRUE**。 如果**FALSE**，沒有重繪就會發生。  
  
### <a name="return-value"></a>傳回值  
 月曆控制項的大小調整為其最小值; 如果為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 呼叫`SizeMinReq`成功顯示整個月曆控制項的一個月的行事曆。  
  
##  <a name="a-namesizerecttomina--cmonthcalctrlsizerecttomin"></a><a name="sizerecttomin"></a>CMonthCalCtrl::SizeRectToMin  
 目前的月份行事曆控制項中，計算的最小矩形可以包含所有符合指定的矩形中的行事曆。  
  
```  
LPRECT SizeRectToMin(LPRECT lpRect);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `lpRect`|指標[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構，定義包含行事曆的所需的數目的矩形。|  
  
### <a name="return-value"></a>傳回值  
 指標[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)所定義的結構定義矩形的大小小於或等於矩形`lpRect`參數。  
  
### <a name="remarks"></a>備註  
 這個方法會計算所指定的矩形所能容納多少行事曆`lpRect`參數，然後傳回可包含行事曆的數字的最小矩形。 實際上，這個方法會縮小以完全符合所需的數目的行事曆的指定的矩形。  
  
 這個方法會傳送[MCM_SIZERECTTOMIN](http://msdn.microsoft.com/library/windows/desktop/bb761020)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 CMNCTRL1](../../visual-cpp-samples.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDateTimeCtrl 類別](../../mfc/reference/cdatetimectrl-class.md)


---
title: "CDateTimeCtrl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDateTimeCtrl
dev_langs:
- C++
helpviewer_keywords:
- DateTimePicker control [MFC], CDateTimeCtrl class
- date-picking functionality
- CDateTimeCtrl class
- DateTimePicker control [MFC]
ms.assetid: 7113993b-5d37-4148-939f-500a190c5bdc
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
ms.openlocfilehash: e5407934021abdb64dfb625e3dfb2c1841b7a5f0
ms.lasthandoff: 02/24/2017

---
# <a name="cdatetimectrl-class"></a>CDateTimeCtrl 類別
封裝日期與時間選擇器控制項的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CDateTimeCtrl : public CWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CDateTimeCtrl::CDateTimeCtrl](#cdatetimectrl)|建構 `CDateTimeCtrl` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CDateTimeCtrl::CloseMonthCal](#closemonthcal)|關閉目前的日期和時間選擇器控制項。|  
|[CDateTimeCtrl::Create](#create)|建立日期和時間選擇器控制項並將它附加`CDateTimeCtrl`物件。|  
|[CDateTimeCtrl::GetDateTimePickerInfo](#getdatetimepickerinfo)|擷取目前的日期和時間選擇器控制項的相關資訊。|  
|[CDateTimeCtrl::GetIdealSize](#getidealsize)|傳回日期和時間選擇器控制項，顯示目前的日期或時間所需的理想大小。|  
|[CDateTimeCtrl::GetMonthCalColor](#getmonthcalcolor)|擷取日期和時間選擇器控制項中的月份行事曆的指定部分的色彩。|  
|[Cdatetimectrl:: Getmonthcalctrl](#getmonthcalctrl)|擷取`CMonthCalCtrl`日期和時間選擇器控制項相關聯的物件。|  
|[CDateTimeCtrl::GetMonthCalFont](#getmonthcalfont)|擷取目前的日期和時間選擇器控制項的子系月曆控制項所使用的字型。|  
|[CDateTimeCtrl::GetMonthCalStyle](#getmonthcalstyle)|取得目前的日期和時間選擇器控制項的樣式。|  
|[CDateTimeCtrl::GetRange](#getrange)|擷取目前的最小和最大允許系統時間的日期和時間選擇器控制項。|  
|[CDateTimeCtrl::GetTime](#gettime)|擷取日期和時間選擇器控制項中目前選取的時間，並將它放在指定的`SYSTEMTIME`結構。|  
|[Cdatetimectrl:: Setformat](#setformat)|設定顯示的日期和時間選擇器控制項根據指定的格式字串。|  
|[CDateTimeCtrl::SetMonthCalColor](#setmonthcalcolor)|設定月曆的日期和時間選擇器控制項中的某個部分的色彩。|  
|[Cdatetimectrl:: Setmonthcalfont](#setmonthcalfont)|設定將會使用日期和時間選擇器控制項的子系月曆控制項的字型。|  
|[CDateTimeCtrl::SetMonthCalStyle](#setmonthcalstyle)|設定目前的日期和時間選擇器控制項的樣式。|  
|[CDateTimeCtrl::SetRange](#setrange)|設定日期和時間選擇器控制項的最小和最大允許的系統時間。|  
|[CDateTimeCtrl::SetTime](#settime)|日期和時間選擇器控制項中設定的時間。|  
  
## <a name="remarks"></a>備註  
 日期和時間選擇器控制項 （DTP 控制項） 提供一個簡單的介面，交換與使用者的日期和時間資訊。 這個介面包含的欄位，其中每個會顯示儲存在該控制項的日期和時間資訊的一部分。 使用者可以變更控制項中儲存的內容中指定欄位的字串的變更資訊。 使用者可以移動欄位的使用滑鼠或鍵盤。  
  
 您可以將各種樣式套用至物件，當您在建立自訂日期和時間選擇器控制項。 請參閱[日期和時間選擇器控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb761728)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]如需有關特定日期和時間選擇器控制項的樣式。 您可以設定使用格式樣式 DTP 控制項的顯示格式。 這些格式樣式中所述在 「 格式樣式 」[!INCLUDE[winsdkshort](../../atl-mfc-shared/reference/includes/winsdkshort_md.md)]主題[日期和時間選擇器控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb761728)。  
  
 日期和時間選擇器控制項也會使用通知和回呼，如下所述[使用 CDateTimeCtrl](../../mfc/using-cdatetimectrl.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CDateTimeCtrl`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxdtctl.h  
  
##  <a name="a-namecdatetimectrla--cdatetimectrlcdatetimectrl"></a><a name="cdatetimectrl"></a>CDateTimeCtrl::CDateTimeCtrl  
 建構 `CDateTimeCtrl` 物件。  
  
```  
CDateTimeCtrl();
```  
  
##  <a name="a-nameclosemonthcala--cdatetimectrlclosemonthcal"></a><a name="closemonthcal"></a>CDateTimeCtrl::CloseMonthCal  
 關閉目前的日期和時間選擇器控制項。  
  
```  
void CloseMonthCal() const;  
```  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[DTM_CLOSEMONTHCAL](http://msdn.microsoft.com/library/windows/desktop/bb761753)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數， `m_dateTimeCtrl`，也就是用來以程式設計方式存取日期和時間選擇器控制項。 下一個範例中會使用此變數。  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s&#1;&1;](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例會關閉目前的日期和時間選擇器控制項的下拉式行事曆。  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s&#1;&5;](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_2.cpp)]  
  
##  <a name="a-namecreatea--cdatetimectrlcreate"></a><a name="create"></a>CDateTimeCtrl::Create  
 建立日期和時間選擇器控制項並將它附加`CDateTimeCtrl`物件。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 `dwStyle`  
 指定日期時間控制項樣式的組合。 請參閱[日期和時間選擇器控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb761728)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]如需有關日期和時間選擇器樣式。  
  
 `rect`  
 參考[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構，也就是日期和時間選擇器控制項的大小與位置。  
  
 `pParentWnd`  
 指標[CWnd](../../mfc/reference/cwnd-class.md)是日期和時間選擇器控制項的父視窗的物件。 它不得為**NULL**。  
  
 `nID`  
 指定日期和時間選擇器控制項的控制項 id。  
  
### <a name="return-value"></a>傳回值  
 非零，如果建立成功。否則為 0。  
  
### <a name="remarks"></a>備註  
  
##### <a name="to-create-a-date-and-time-picker-control"></a>若要建立的日期和時間選擇器控制項  
  
1.  呼叫[CDateTimeCtrl](#cdatetimectrl)建構`CDateTimeCtrl`物件。  
  
2.  呼叫此成員函式，建立 Windows 日期和時間選擇器控制項並將它附加`CDateTimeCtrl`物件。  
  
 當您呼叫**建立**，通用控制項都已初始化。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CDateTimeCtrl #&1;](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_3.cpp)]  
  
##  <a name="a-namegetdatetimepickerinfoa--cdatetimectrlgetdatetimepickerinfo"></a><a name="getdatetimepickerinfo"></a>CDateTimeCtrl::GetDateTimePickerInfo  
 擷取目前的日期和時間選擇器控制項的相關資訊。  
  
```   
BOOL GetDateTimePickerInfo(LPDATETIMEPICKERINFO pDateTimePickerInfo) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[輸出] `pDateTimePickerInfo`|指標[DATETIMEPICKERINFO](http://msdn.microsoft.com/library/windows/desktop/bb761729)結構會接收目前的日期和時間選擇器控制項的描述。<br /><br /> 呼叫端會負責配置這個結構。 不過，這個方法會初始化`cbSize`結構的成員。|  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[DTM_GETDATETIMEPICKERINFO](http://msdn.microsoft.com/library/windows/desktop/bb761755)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數， `m_dateTimeCtrl`，也就是用來以程式設計方式存取日期和時間選擇器控制項。 下一個範例中會使用此變數。  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s&#1;&1;](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例指出它是否已成功擷取目前的日期和時間選擇器控制項的相關資訊。  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s&#1;&4;](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_4.cpp)]  
  
##  <a name="a-namegetmonthcalcolora--cdatetimectrlgetmonthcalcolor"></a><a name="getmonthcalcolor"></a>CDateTimeCtrl::GetMonthCalColor  
 擷取日期和時間選擇器控制項中的月份行事曆的指定部分的色彩。  
  
```  
COLORREF GetMonthCalColor(int iColor) const;  
```  
  
### <a name="parameters"></a>參數  
 `iColor`  
 `int`值，指定要擷取的月曆色彩區域。 如需值的清單，請參閱`iColor`參數[SetMonthCalColor](#setmonthcalcolor)。  
  
### <a name="return-value"></a>傳回值  
 A **COLORREF**如果成功，表示月曆控制項的指定部分的色彩設定的值。 如果不成功，函式會傳回-1。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[DTM_GETMCCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb761759)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CDateTimeCtrl #&2;](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_5.cpp)]  
  
##  <a name="a-namegetmonthcalctrla--cdatetimectrlgetmonthcalctrl"></a><a name="getmonthcalctrl"></a>Cdatetimectrl:: Getmonthcalctrl  
 擷取`CMonthCalCtrl`日期和時間選擇器控制項相關聯的物件。  
  
```  
CMonthCalCtrl* GetMonthCalCtrl() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標[CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)物件，或**NULL**如果不成功，或如果看不到視窗。  
  
### <a name="remarks"></a>備註  
 日期和時間選擇器控制項建立子月曆控制項，當使用者按一下下拉箭號。 當`CMonthCalCtrl`不再需要物件、 被損毀，因此您的應用程式必須依賴儲存物件，代表日期時間選擇器控制項的子系月曆。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CDateTimeCtrl #&3;](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_6.cpp)]  
  
##  <a name="a-namegetmonthcalfonta--cdatetimectrlgetmonthcalfont"></a><a name="getmonthcalfont"></a>CDateTimeCtrl::GetMonthCalFont  
 取得目前的日期和時間選擇器控制項的月曆控制項所使用的字型。  
  
```  
CFont* GetMonthCalFont() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標[CFont](../../mfc/reference/cfont-class.md)物件，或**NULL**如果不成功。  
  
### <a name="remarks"></a>備註  
 `CFont`所指之傳回值的物件是暫存物件，並且被終結在下一步的閒置處理時間。  
  
##  <a name="a-namegetmonthcalstylea--cdatetimectrlgetmonthcalstyle"></a><a name="getmonthcalstyle"></a>CDateTimeCtrl::GetMonthCalStyle  
 取得下拉式月曆控制項與目前的日期和時間選擇器控制項相關聯的樣式。  
  
```  
DWORD GetMonthCalStyle() const;  
```  
  
### <a name="return-value"></a>傳回值  
 樣式下拉式月曆控制項，也就是位元的組合 （或者） 的日期和時間選擇器控制項的樣式。 如需詳細資訊，請參閱[月份行事曆控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760919)。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[DTM_GETMCSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb761763)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetrangea--cdatetimectrlgetrange"></a><a name="getrange"></a>CDateTimeCtrl::GetRange  
 擷取目前的最小和最大允許系統時間的日期和時間選擇器控制項。  
  
```  
DWORD GetRange(
    COleDateTime* pMinRange,  
    COleDateTime* pMaxRange) const;  
  
DWORD GetRange(
    CTime* pMinRange,  
    CTime* pMaxRange) const;  
```  
  
### <a name="parameters"></a>參數  
 `pMinRange`  
 指標[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件或[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件，其中包含在允許的最早時間`CDateTimeCtrl`物件。  
  
 `pMaxRange`  
 指標`COleDateTime`物件或`CTime`物件，其中包含在允許的最晚時間`CDateTimeCtrl`物件。  
  
### <a name="return-value"></a>傳回值  
 A`DWORD`包含指出哪些範圍已設定的旗標的值。 如果  
  
 `return value & GDTR_MAX` == 0  
  
 然後第二個參數才有效。 同樣地，如果  
  
 `return value & GDTR_MIN` == 0  
  
 然後第一個參數是有效的。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[DTM_GETRANGE](http://msdn.microsoft.com/library/windows/desktop/bb761767)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 在 MFC 的實作中，您可以指定`COleDateTime`或`CTime`的使用方式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CDateTimeCtrl #&4;](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_7.cpp)]  
  
##  <a name="a-namegettimea--cdatetimectrlgettime"></a><a name="gettime"></a>CDateTimeCtrl::GetTime  
 擷取日期和時間選擇器控制項中目前選取的時間，並將它放在指定的`SYSTEMTIME`結構。  
  
```  
BOOL GetTime(COleDateTime& timeDest) const;  
DWORD GetTime(CTime& timeDest) const;  
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;  
```  
  
### <a name="parameters"></a>參數  
 *timeDest*  
 第一版的參考[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)將會收到系統時間資訊的物件。 在第二個版本中，參考[CTime](../../atl-mfc-shared/reference/ctime-class.md)將會收到系統時間資訊的物件。  
  
 *pTimeDest*  
 指標[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)接收系統時間資訊的結構。 不能**NULL**。  
  
### <a name="return-value"></a>傳回值  
 在第一個版本中，如果要成功寫入的時間為非零`COleDateTime`物件，否則傳回 0。 在第二個和第三個版本中，`DWORD`值等於**dwFlag**成員集中[NMDATETIMECHANGE](http://msdn.microsoft.com/library/windows/desktop/bb761730)結構。 請參閱**備註**如需詳細資訊，如下一節。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[DTM_GETSYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/bb761769)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 在 MFC 實作**GetTime**，您可以使用`COleDateTime`或`CTime`類別，或者您可以使用`SYSTEMTIME`結構，來儲存時間資訊。  
  
 傳回值`DWORD`在第二個和第三個版本中，上述方式，表示日期和時間選擇器控制項是否設定為 「 沒有日期 」 狀態，如下所示[NMDATETIMECHANGE](http://msdn.microsoft.com/library/windows/desktop/bb761730)結構成員`dwFlags`。 如果傳回的值等於**GDT_NONE**，控制項設定為 「 沒有日期 」 狀態，並使用**DTS_SHOWNONE**樣式。 如果傳回的值等於**GDT_VALID**，系統時間已成功儲存在目的地位置。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CDateTimeCtrl #&5;](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_8.cpp)]  
  
##  <a name="a-namegetidealsizea--cdatetimectrlgetidealsize"></a><a name="getidealsize"></a>CDateTimeCtrl::GetIdealSize  
 傳回日期和時間選擇器控制項，顯示目前的日期或時間所需的理想大小。  
  
```  
BOOL GetIdealSize(LPSIZE psize) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[輸出] `psize`|指標[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)結構，包含控制項的理想大小。|  
  
### <a name="return-value"></a>傳回值  
 傳回值永遠是`true`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[DTM_GETIDEALSIZE](http://msdn.microsoft.com/library/windows/desktop/bb761757)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數， `m_dateTimeCtrl`，也就是用來以程式設計方式存取日期和時間選擇器控制項。 下一個範例中會使用此變數。  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s&#1;&1;](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例會擷取顯示日期和時間選擇器控制項的理想大小。  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s&#1;&2;](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_9.cpp)]  
  
##  <a name="a-namesetformata--cdatetimectrlsetformat"></a><a name="setformat"></a>Cdatetimectrl:: Setformat  
 設定顯示的日期和時間選擇器控制項根據指定的格式字串。  
  
```  
BOOL SetFormat(LPCTSTR pstrFormat);
```  
  
### <a name="parameters"></a>參數  
 *pstrFormat*  
 定義所要的顯示零結尾的格式字串的指標。 此參數設定為**NULL**會將控制項重設目前的樣式的預設格式字串。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
> [!NOTE]
>  使用者輸入不會判斷成功或失敗，此呼叫。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[DTM_SETFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb761771)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CDateTimeCtrl #&6;](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_10.cpp)]  
  
##  <a name="a-namesetmonthcalcolora--cdatetimectrlsetmonthcalcolor"></a><a name="setmonthcalcolor"></a>CDateTimeCtrl::SetMonthCalColor  
 設定月曆的日期和時間選擇器控制項中的某個部分的色彩。  
  
```  
COLORREF SetMonthCalColor(
    int iColor,  
    COLORREF ref);
```  
  
### <a name="parameters"></a>參數  
 `iColor`  
 `int`值，指定設定月曆控制項的哪個區域。 這個值可以是下列其中一個項目。  
  
|值|意義|  
|-----------|-------------|  
|MCSC_BACKGROUND|設定背景色彩顯示幾個月之間。|  
|MCSC_MONTHBK|設定每個月內顯示的背景色彩。|  
|MCSC_TEXT|設定用來顯示每個月內文字的色彩。|  
|MCSC_TITLEBK|設定行事曆的標題中顯示的背景色彩。|  
|MCSC_TITLETEXT|設定用來顯示行事曆的標題中文字的色彩。|  
|MCSC_TRAILINGTEXT|設定用來顯示標頭和結尾的日期文字的色彩。 標頭和結尾天數是從目前的行事曆會出現之前與之後月份的天數。|  
  
 `ref`  
 A **COLORREF**值，表示將月份行事曆的指定區域的色彩。  
  
### <a name="return-value"></a>傳回值  
 A **COLORREF**值，如果成功，表示月曆控制項的指定部分原來的色彩設定。 否則，訊息會傳回-1。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[DTM_SETMCCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb761773)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[CDateTimeCtrl::GetMonthCalColor](#getmonthcalcolor)。  
  
##  <a name="a-namesetmonthcalfonta--cdatetimectrlsetmonthcalfont"></a><a name="setmonthcalfont"></a>Cdatetimectrl:: Setmonthcalfont  
 設定將會使用日期和時間選擇器控制項的子系月曆控制項的字型。  
  
```  
void SetMonthCalFont(
    HFONT hFont,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `hFont`  
 將字型的控制代碼。  
  
 `bRedraw`  
 指定是否在控制項應該立即更新時設定字型。 此參數設定為**TRUE**會使控制項重繪其本身。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[DTM_SETMCFONT](http://msdn.microsoft.com/library/windows/desktop/bb761775)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CDateTimeCtrl #&7;](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_11.cpp)]  
  
> [!NOTE]
>  如果您使用此程式碼，您要將您`CDialog`-衍生類別呼叫`m_MonthFont`型別的**CFont**。  
  
##  <a name="a-namesetmonthcalstylea--cdatetimectrlsetmonthcalstyle"></a><a name="setmonthcalstyle"></a>CDateTimeCtrl::SetMonthCalStyle  
 設定下拉式月曆控制項與目前的日期和時間選擇器控制項相關聯的樣式。  
  
```  
DWORD SetMonthCalStyle(DWORD dwStyle);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `dwStyle`|新的月份行事曆控制項樣式，也就是每月的行事曆控制項樣式位元組合 (OR)。 如需詳細資訊，請參閱[月份行事曆控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760919)。|  
  
### <a name="return-value"></a>傳回值  
 上一個下拉式月曆控制項的樣式。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[DTM_SETMCSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb761778)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數， `m_dateTimeCtrl`，也就是用來以程式設計方式存取日期和時間選擇器控制項。 下一個範例中會使用此變數。  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s&#1;&1;](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例會設定日期和時間選擇器控制項來顯示週數、 每週和任何今日指標的時代的縮寫名稱。  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s&#1;&3;](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_12.cpp)]  
  
##  <a name="a-namesetrangea--cdatetimectrlsetrange"></a><a name="setrange"></a>CDateTimeCtrl::SetRange  
 設定日期和時間選擇器控制項的最小和最大允許的系統時間。  
  
```  
BOOL SetRange(
    const COleDateTime* pMinRange,  
    const COleDateTime* pMaxRange);

 
BOOL SetRange(
    const CTime* pMinRange,  
    const CTime* pMaxRange);
```  
  
### <a name="parameters"></a>參數  
 `pMinRange`  
 指標[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件或[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件，其中包含在允許的最早時間`CDateTimeCtrl`物件。  
  
 `pMaxRange`  
 指標`COleDateTime`物件或`CTime`物件，其中包含在允許的最晚時間`CDateTimeCtrl`物件。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[DTM_SETRANGE](http://msdn.microsoft.com/library/windows/desktop/bb761780)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 在 MFC 的實作中，您可以指定`COleDateTime`或`CTime`的使用方式。 如果`COleDateTime`物件具有**NULL**狀態，將會移除範圍。 如果`CTime`指標或`COleDateTime`指標**NULL**，將會移除範圍。  
  
### <a name="example"></a>範例  
  請參閱範例[CDateTimeCtrl::GetRange](#getrange)。  
  
##  <a name="a-namesettimea--cdatetimectrlsettime"></a><a name="settime"></a>CDateTimeCtrl::SetTime  
 日期和時間選擇器控制項中設定的時間。  
  
```  
BOOL SetTime(const COleDateTime& timeNew);  
BOOL SetTime(const CTime* pTimeNew);  
BOOL SetTime(LPSYSTEMTIME pTimeNew = NULL);
```  
  
### <a name="parameters"></a>參數  
 *timeNew*  
 參考[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件，包含控制項設定。  
  
 *pTimeNew*  
 在上面的指標，第二個版本[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件，其中包含要將設定控制項的時間。 在第三個版本以上的指標[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)結構，其中包含要將設定控制項的時間。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[DTM_SETSYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/bb761782)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 在 MFC 實作**SetTime**，您可以使用`COleDateTime`或`CTime`類別，或者您可以使用`SYSTEMTIME`結構，來設定的時間資訊。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CDateTimeCtrl #&8;](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_13.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 CMNCTRL1](../../visual-cpp-samples.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CMonthCalCtrl 類別](../../mfc/reference/cmonthcalctrl-class.md)


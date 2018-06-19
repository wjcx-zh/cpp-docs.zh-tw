---
title: CTimeSpan 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CTimeSpan
- ATLTIME/ATL::CTimeSpan
- ATLTIME/ATL::CTimeSpan::CTimeSpan
- ATLTIME/ATL::CTimeSpan::Format
- ATLTIME/ATL::CTimeSpan::GetDays
- ATLTIME/ATL::CTimeSpan::GetHours
- ATLTIME/ATL::CTimeSpan::GetMinutes
- ATLTIME/ATL::CTimeSpan::GetSeconds
- ATLTIME/ATL::CTimeSpan::GetTimeSpan
- ATLTIME/ATL::CTimeSpan::GetTotalHours
- ATLTIME/ATL::CTimeSpan::GetTotalMinutes
- ATLTIME/ATL::CTimeSpan::GetTotalSeconds
- ATLTIME/ATL::CTimeSpan::Serialize64
dev_langs:
- C++
helpviewer_keywords:
- elapsed time, CTimeSpan object
- timespan
- time span
- CTimeSpan class
- shared classes, CTimeSpan
- time, elapsed
ms.assetid: ee1e42f6-1839-477a-8435-fb26ad475140
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd95d26dd2df41f16091379c892f67319c218cc4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365314"
---
# <a name="ctimespan-class"></a>CTimeSpan 類別
在內部儲存為時間範圍中的秒數的時間量。  
  
## <a name="syntax"></a>語法  
  
```
class CTimeSpan
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CTimeSpan::CTimeSpan](#ctimespan)|建構`CTimeSpan`物件以各種方式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CTimeSpan::Format](#format)|將轉換`CTimeSpan`成格式化字串。|  
|[CTimeSpan::GetDays](#getdays)|傳回值，這個值表示在這個完成的天數`CTimeSpan`。|  
|[CTimeSpan::GetHours](#gethours)|傳回表示目前的日期 (-23 到 23) 的時數的值。|  
|[CTimeSpan::GetMinutes](#getminutes)|傳回值，表示目前的小時 (-59 到 59) 中的分鐘數。|  
|[CTimeSpan::GetSeconds](#getseconds)|傳回值，表示在目前的分鐘 (-59 到 59) 的秒數。|  
|[CTimeSpan::GetTimeSpan](#gettimespan)|傳回的值`CTimeSpan`物件。|  
|[CTimeSpan::GetTotalHours](#gettotalhours)|傳回值，這個值表示在這個完成的時數的總數`CTimeSpan`。|  
|[CTimeSpan::GetTotalMinutes](#gettotalminutes)|傳回值，這個值表示在這個完成的分鐘總數`CTimeSpan`。|  
|[CTimeSpan::GetTotalSeconds](#gettotalseconds)|傳回值，這個值表示在這個完成的秒數的總數`CTimeSpan`。|  
|[CTimeSpan::Serialize64](#serialize64)|將序列化資料，或從封存。|  
  
### <a name="operators"></a>運算子  
  
|||  
|-|-|  
|[運算子 +-](#operator_add_-)|加入和減去`CTimeSpan`物件。|  
|[運算子 + = =](#operator_add_eq_-_eq)|加入和減去`CTimeSpan`物件與此`CTimeSpan`。|  
|[運算子 = = < 等等。](#ctimespan_comparison_operators)|比較兩個相對的時間值。|  
  
## <a name="remarks"></a>備註  
 `CTimeSpan` 沒有基底類別。  
  
 `CTimeSpan` 函數會將轉換為各種組合的天數、 小時、 分鐘、 秒數以及。  
  
 `CTimeSpan`物件會儲存在 **__time64_t**結構，也就是 8 個位元組。  
  
 附屬類別[CTime](../../atl-mfc-shared/reference/ctime-class.md)，代表絕對時間。  
  
 `CTime`和`CTimeSpan`類別不設計供衍生。 因為沒有虛擬函式，這兩者的大小`CTime`和`CTimeSpan`物件是完全 8 個位元組。 大部分成員函式會以內嵌方式。  
  
 如需有關使用`CTimeSpan`，請參閱文章[日期和時間](../../atl-mfc-shared/date-and-time.md)，和[時間管理](../../c-runtime-library/time-management.md)中*執行階段程式庫參考*。  
  
## <a name="requirements"></a>需求  
 **標頭：** atltime.h  
  
##  <a name="ctimespan_comparison_operators"></a>  CTimeSpan 比較運算子  
 比較運算子。  
  
```
bool operator==(CTimeSpan span) const throw();
bool operator!=(CTimeSpan span) const throw();
bool operator<(CTimeSpan span) const throw();
bool operator>(CTimeSpan span) const throw();
bool operator<=(CTimeSpan span) const throw();
bool operator>=(CTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>參數  
 `span`  
  
 要比較的物件。  
  
### <a name="return-value"></a>傳回值  
 這些運算子比較兩個相對的時間值。 它們會傳回**true**如果條件為 true，否則**false**。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#169](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_1.cpp)]  
  
##  <a name="ctimespan"></a>  CTimeSpan::CTimeSpan  
 建構`CTimeSpan`物件以各種方式。  
  
```
CTimeSpan() throw();
CTimeSpan(__time64_t time) throw();

CTimeSpan(  
 LONG lDays,
 int nHours,
 int nMins,
 int nSecs) throw();
```  
  
### <a name="parameters"></a>參數  
 *timeSpanSrc*  
 A`CTimeSpan`已經存在的物件。  
  
 `time`  
 A **__time64_t**時間值，這是中的時間範圍秒數。  
  
 `lDays`、`nHours`、`nMins``nSecs`  
 天、 小時、 分鐘，並分別秒數。  
  
### <a name="remarks"></a>備註  
 所有這些建構函式建立新`CTimeSpan`以指定的相對時間初始化的物件。 下面會描述每個建構函式：  
  
- **CTimeSpan （);** 建構未初始化`CTimeSpan`物件。  
  
- **CTimeSpan (const CTimeSpan （& s));** 建構`CTimeSpan`從另一個物件`CTimeSpan`值。  
  
- **CTimeSpan (__time64_t);** 建構`CTimeSpan`物件從 **__time64_t**型別。  
  
- **CTimeSpan (長**， **int，int，int);** 建構`CTimeSpan`物件與每個元件的元件從受限於下列範圍：  
  
    |元件|範圍|  
    |---------------|-----------|  
    |`lDays`|0-25000 （大約）|  
    |`nHours`|0-23|  
    |`nMins`|0-59|  
    |`nSecs`|0-59|  
  
 請注意，偵錯版本的 Mfc 程式庫判斷提示，如果一個或多個當天時間元件超出範圍。 您必須負責驗證之前呼叫的引數。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#162](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_2.cpp)]  
  
##  <a name="format"></a>  CTimeSpan::Format  
 產生對應至這個的格式化的字串`CTimeSpan`。  
  
```
CString Format(LPCSTR pFormat) const;
CString Format(LPCTSTR pszFormat) const;
CString Format(UINT nID) const;
```  
  
### <a name="parameters"></a>參數  
 `pFormat`, `pszFormat`  
 格式字串類似於`printf`格式化字串。 格式化程式碼，加上百分比 ( `%`) 登入，對應會取代`CTimeSpan`元件。 格式字串中的其他字元都會複製到傳回的字串不變。 值和的格式化程式碼的意義**格式**如下所示：  
  
- **%D**總這中的天數 `CTimeSpan`  
  
- **%H**當天的時數  
  
- **%M**分鐘在目前的小時  
  
- **%S**中目前的分鐘數的秒數  
  
- **%%** 百分比符號  
  
 `nID`  
 識別此格式的字串識別碼。  
  
### <a name="return-value"></a>傳回值  
 A`CString`物件，其中包含格式的時間。  
  
### <a name="remarks"></a>備註  
 程式庫的偵錯版本會檢查格式的程式碼，並判斷提示程式碼是否不在上述清單中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#163](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_3.cpp)]  
  
##  <a name="getdays"></a>  CTimeSpan::GetDays  
 傳回值，這個值表示在這個完成的天數`CTimeSpan`。  
  
```
LONGLONG GetDays() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回天數完成 24 小時制的時間範圍中。 這個值可以是負數，如果時間範圍為負數。  
  
### <a name="remarks"></a>備註  
 請注意，日光節約時間可能會導致`GetDays`傳回可能令人意外的結果。 例如，當 DST 是作用中， **GetDays**報表年 4 月 1 與 5 月 1 日之間的天數會做 29，不是 30，因為一天在四月縮短一小時，因此不會計算為完整的一天。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#164](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_4.cpp)]  
  
##  <a name="gethours"></a>  CTimeSpan::GetHours  
 傳回表示目前的日期 (-23 到 23) 的時數的值。  
  
```
LONG GetHours() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回目前日期的小時數。 範圍是從-23 到 23。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#165](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_5.cpp)]  
  
##  <a name="getminutes"></a>  CTimeSpan::GetMinutes  
 傳回值，表示目前的小時 (-59 到 59) 中的分鐘數。  
  
```
LONG GetMinutes() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回目前的小時中的分鐘數。 範圍是從-59 到 59。  
  
### <a name="example"></a>範例  
 請參閱範例的[GetHours](#gethours)。  
  
##  <a name="getseconds"></a>  CTimeSpan::GetSeconds  
 傳回值，表示在目前的分鐘 (-59 到 59) 的秒數。  
  
```
LONG GetSeconds() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回在目前的分鐘的秒數。 範圍是從-59 到 59。  
  
### <a name="example"></a>範例  
 請參閱範例的[GetHours](#gethours)。  
  
##  <a name="gettimespan"></a>  CTimeSpan::GetTimeSpan  
 傳回的值`CTimeSpan`物件。  
  
```
__ time64_t GetTimeSpan() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回目前的值`CTimeSpan`物件。  
  
##  <a name="gettotalhours"></a>  CTimeSpan::GetTotalHours  
 傳回值，這個值表示在這個完成的時數的總數`CTimeSpan`。  
  
```
LONGLONG GetTotalHours() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回在這個完成的總時數`CTimeSpan`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#166](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_6.cpp)]  
  
##  <a name="gettotalminutes"></a>  CTimeSpan::GetTotalMinutes  
 傳回值，這個值表示在這個完成的分鐘總數`CTimeSpan`。  
  
```
LONGLONG GetTotalMinutes() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 在此傳回總完成的分鐘數`CTimeSpan`。  
  
### <a name="example"></a>範例  
 請參閱範例的[GetTotalHours](#gettotalhours)。  
  
##  <a name="gettotalseconds"></a>  CTimeSpan::GetTotalSeconds  
 傳回值，這個值表示在這個完成的秒數的總數`CTimeSpan`。  
  
```
LONGLONG GetTotalSeconds() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 在此傳回總完成的秒數`CTimeSpan`。  
  
### <a name="example"></a>範例  
 請參閱範例的[GetTotalHours](#gettotalhours)。  
  
##  <a name="operator_add_-"></a>  CTimeSpan::operator +、-  
 加入和減去`CTimeSpan`物件。  
  
```
CTimeSpan operator+(CTimeSpan span) const throw();
CTimeSpan operator-(CTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>參數  
 `span`  
 要加入值`CTimeSpan`物件。  
  
### <a name="return-value"></a>傳回值  
 A`CTimeSpan`物件，代表作業的結果。  
  
### <a name="remarks"></a>備註  
 這兩個運算子可讓您加入和減去`CTimeSpan`物件彼此。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#167](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_7.cpp)]  
  
##  <a name="operator_add_eq_-_eq"></a>  CTimeSpan::operator + =、-= 左邊  
 加入和減去`CTimeSpan`物件與此`CTimeSpan`。  
  
```
CTimeSpan& operator+=(CTimeSpan span) throw();
CTimeSpan& operator-=(CTimeSpan span) throw();
```  
  
### <a name="parameters"></a>參數  
 `span`  
 要加入值`CTimeSpan`物件。  
  
### <a name="return-value"></a>傳回值  
 已更新`CTimeSpan`物件。  
  
### <a name="remarks"></a>備註  
 這些運算子可讓您加入和減去`CTimeSpan`物件與此`CTimeSpan`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities#168](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_8.cpp)]  
  
##  <a name="serialize64"></a>  CTimeSpan::Serialize64  
  
> [!NOTE]
>  這個方法僅適用於 MFC 專案。  
  
 將序列化相關聯的成員變數，或從封存的資料。  
  
```
CArchive& Serialize64(CArchive& ar);
```  
  
### <a name="parameters"></a>參數  
 `ar`  
 `CArchive`您想要更新的物件。  
  
### <a name="return-value"></a>傳回值  
 已更新`CArchive`物件。  
  
## <a name="see-also"></a>另請參閱  
 [asctime、_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [_ftime、_ftime32、_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime、_gmtime32、_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime、_localtime32、_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [strftime、wcsftime、_strftime_l、_wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)   
 [time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)



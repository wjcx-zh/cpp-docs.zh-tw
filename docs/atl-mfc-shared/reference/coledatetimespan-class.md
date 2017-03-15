---
title: "COleDateTimeSpan 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.COleDateTimeSpan
- COleDateTimeSpan
- ATL::COleDateTimeSpan
dev_langs:
- C++
helpviewer_keywords:
- timespan
- time span
- shared classes, COleDateTimeSpan
- Date data type, MFC encapsulation of
- COleDateTimeSpan class
ms.assetid: 7441526d-a30a-4019-8fb3-3fee6f897cbe
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 4091ca2c766d56d8398119413778af0a0405b8ab
ms.lasthandoff: 02/24/2017

---
# <a name="coledatetimespan-class"></a>COleDateTimeSpan 類別
代表相對的時間，時間範圍。  
  
## <a name="syntax"></a>語法  
  
```
class COleDateTimeSpan
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[COleDateTimeSpan::COleDateTimeSpan](#coledatetimespan)|建構 `COleDateTimeSpan` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[COleDateTimeSpan::Format](#format)|產生的格式化的字串表示`COleDateTimeSpan`物件。|  
|[COleDateTimeSpan::GetDays](#getdays)|這會傳回日期的部份範圍`COleDateTimeSpan`物件代表。|  
|[COleDateTimeSpan::GetHours](#gethours)|這會傳回不同時間的小時部分`COleDateTimeSpan`物件代表。|  
|[COleDateTimeSpan::GetMinutes](#getminutes)|這會傳回的分鐘部分之範圍`COleDateTimeSpan`物件代表。|  
|[COleDateTimeSpan::GetSeconds](#getseconds)|這會傳回範圍的第二個部分`COleDateTimeSpan`物件代表。|  
|[COleDateTimeSpan::GetStatus](#getstatus)|取得此狀態 （有效性）`COleDateTimeSpan`物件。|  
|[COleDateTimeSpan::GetTotalDays](#gettotaldays)|傳回此天數`COleDateTimeSpan`物件代表。|  
|[COleDateTimeSpan::GetTotalHours](#gettotalhours)|這會傳回小時數`COleDateTimeSpan`物件代表。|  
|[COleDateTimeSpan::GetTotalMinutes](#gettotalminutes)|這會傳回的分鐘數`COleDateTimeSpan`物件代表。|  
|[COleDateTimeSpan::GetTotalSeconds](#gettotalseconds)|這會傳回的秒數`COleDateTimeSpan`物件代表。|  
|[COleDateTimeSpan::SetDateTimeSpan](#setdatetimespan)|設定這個值`COleDateTimeSpan`物件。|  
|[COleDateTimeSpan::SetStatus](#setstatus)|設定狀態 （有效性） 這個`COleDateTimeSpan`物件。|  
  
### <a name="public-operators"></a>公用運算子  
  
|||  
|-|-|  
|[運算子 +、-](#operator_add_-)|新增、 相減，以及變更符號`COleDateTimeSpan`值。|  
|[運算子 + =、 =](#operator_add_eq_-_eq)|加號和減號運算子`COleDateTimeSpan`值從這個`COleDateTimeSpan`值。|  
|[運算子 =](#operator_eq)|複製`COleDateTimeSpan`值。|  
|[運算子 = =、<,></,><>](#coledatetimespan_relational_operators)|比較兩個`COleDateTimeSpan`值。|  
|[運算子 double](#operator_double)|此轉換`COleDateTimeSpan`值**雙**。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[COleDateTimeSpan::m_span](#m_span)|包含基礎**雙**這個`COleDateTimeSpan`物件。|  
|[COleDateTimeSpan::m_status](#m_status)|包含這個狀態`COleDateTimeSpan`物件。|  
  
## <a name="remarks"></a>備註  
 `COleDateTimeSpan`沒有基底類別。  
  
 A`COleDateTimeSpan`持續時間，以天為單位。  
  
 `COleDateTimeSpan`搭配其附屬類別[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)。 `COleDateTime`封裝**日期**OLE automation 資料類型。 `COleDateTime`表示絕對時間值。 所有`COleDateTime`計算涉及`COleDateTimeSpan`值。 這些類別之間的關聯性相當於間[CTime](../../atl-mfc-shared/reference/ctime-class.md)和[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)。  
  
 如需有關`COleDateTime`和`COleDateTimeSpan`類別，請參閱文章[日期和時間︰ 自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)。  
  
## <a name="requirements"></a>需求  
 **標頭︰** ATLComTime.h  
  
##  <a name="a-namecoledatetimespanrelationaloperatorsa--coledatetimespan-relational-operators"></a><a name="coledatetimespan_relational_operators"></a>COleDateTimeSpan 關係運算子  
 比較運算子。  
  
```
bool operator==(const COleDateTimeSpan& dateSpan) const throw();
bool operator!=(const COleDateTimeSpan& dateSpan) const throw();
bool operator<(const COleDateTimeSpan& dateSpan) const throw();
bool operator>(const COleDateTimeSpan& dateSpan) const throw();
bool operator<=(const COleDateTimeSpan& dateSpan) const throw();
bool operator>=(const COleDateTimeSpan& dateSpan) const throw();
```  
  
### <a name="parameters"></a>參數  
 *dateSpan*  
 要比較的 `COleDateTimeSpan`。  
  
### <a name="return-value"></a>傳回值  
 這些運算子比較兩個日期/時間值，並傳回**true**如果條件為 true，否則**false**。  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  如果任一個運算元無效，就會發生 ATLASSERT。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&25;](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_1.cpp)]  
  
 [!code-cpp[NVC_ATLMFC_Utilities #&26;](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_2.cpp)]  
  
##  <a name="a-namecoledatetimespana--coledatetimespancoledatetimespan"></a><a name="coledatetimespan"></a>COleDateTimeSpan::COleDateTimeSpan  
 建構 `COleDateTimeSpan` 物件。  
  
```
COleDateTimeSpan() throw();
COleDateTimeSpan(double dblSpanSrc) throw();
COleDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```  
  
### <a name="parameters"></a>參數  
 `dblSpanSrc`  
 若要複製到新的天數`COleDateTimeSpan`物件。  
  
 `lDays`, `nHours`, `nMins`, `nSecs`  
 表示要複製到新的日期和時間值`COleDateTimeSpan`物件。  
  
### <a name="remarks"></a>備註  
 所有這些建構函式建立新的`COleDateTimeSpan`物件初始化為指定的值。 每個建構函式的簡短描述如下︰  
  
- **COleDateTimeSpan （)**建構`COleDateTimeSpan`物件初始化為 0。  
  
- **COleDateTimeSpan (** `dblSpanSrc` **)**建構`COleDateTimeSpan`浮點值的物件。  
  
- **COleDateTimeSpan (** `lDays` **，** `nHours` **，** `nMins` **，** `nSecs` **)**建構`COleDateTimeSpan`物件初始化為指定的數值。  
  
 新的狀態`COleDateTimeSpan`物件設為有效。  
  
 如需有關界限`COleDateTimeSpan`值，請參閱文章[日期和時間︰ 自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&14;](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_3.cpp)]  
  
##  <a name="a-nameformata--coledatetimespanformat"></a><a name="format"></a>COleDateTimeSpan::Format  
 產生的格式化的字串表示`COleDateTimeSpan`物件。  
  
```
CString Format(LPCTSTR pFormat) const;
CString Format(UINT nID) const;
```  
  
### <a name="parameters"></a>參數  
 `pFormat`  
 格式化字串類似於`printf`格式化字串。 格式化程式碼，加上百分比 ( `%`) 登入，對應會取代`COleDateTimeSpan`元件。 格式化字串中的其他字元都會複製到傳回的字串不變。 值和意義的格式化程式碼**格式**如下所示︰  
  
- **%H**當天的時數  
  
- **%M**目前的小時的分鐘數  
  
- **%S**目前這一分鐘的秒數  
  
- **%%**百分比符號  
  
 四個以上所列的格式化程式碼的格式將接受的唯一代碼。  
  
-  
  
 `nID`  
 格式控制字串資源識別碼。  
  
### <a name="return-value"></a>傳回值  
 A `CString` ，其中包含已格式化的日期/時間範圍值。  
  
### <a name="remarks"></a>備註  
 呼叫這些函式來建立格式化的表示法的時間範圍值。 如果這個狀態`COleDateTimeSpan`物件為 null，則傳回值為空字串。 如果狀態不正確，則傳回字串由字串資源**IDS_INVALID_DATETIMESPAN**。  
  
 此函式之表單的簡短描述如下︰  
  
 **Format(** `pFormat` **)**  
 此表單會使用格式字串，其中包含特殊格式化的程式碼會加上百分比符號 （%），將值格式化中`printf`。 格式化字串做為參數傳遞至函式。  
  
 **Format(** `nID` **)**  
 此表單會使用格式字串，其中包含特殊格式化的程式碼會加上百分比符號 （%），將值格式化中`printf`。 格式化字串則為資源。 此字串資源的識別碼會當做參數傳遞。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&15;](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_4.cpp)]  
  
##  <a name="a-namegetdaysa--coledatetimespangetdays"></a><a name="getdays"></a>COleDateTimeSpan::GetDays  
 擷取此日期/時間值的日數部分。  
  
```
LONG GetDays() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 此日期/時間值的日數部分。  
  
### <a name="remarks"></a>備註  
 傳回值之間的這個函式範圍從大約 – 3,615,000 和 3,615,000。  
  
 其他函式的查詢的值`COleDateTimeSpan`物件，請參閱下列的成員函式︰  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&16;](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_5.cpp)]  
  
##  <a name="a-namegethoursa--coledatetimespangethours"></a><a name="gethours"></a>COleDateTimeSpan::GetHours  
 擷取此日期/時間值的小時部分。  
  
```
LONG GetHours() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 此日期/時間值的小時部分。  
  
### <a name="remarks"></a>備註  
 傳回這個-23 到 23 之間的函式範圍的值。  
  
 其他函式的查詢的值`COleDateTimeSpan`物件，請參閱下列的成員函式︰  
  
- [GetDays](#getdays)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&17;](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_6.cpp)]  
  
##  <a name="a-namegetminutesa--coledatetimespangetminutes"></a><a name="getminutes"></a>COleDateTimeSpan::GetMinutes  
 擷取此日期/時間值的分鐘部分。  
  
```
LONG GetMinutes() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 此日期/時間值的分鐘部分。  
  
### <a name="remarks"></a>備註  
 傳回的值從-59 到 59 之間的這個函式範圍。  
  
 其他函式的查詢的值`COleDateTimeSpan`物件，請參閱下列的成員函式︰  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&18;](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_7.cpp)]  
  
##  <a name="a-namegetsecondsa--coledatetimespangetseconds"></a><a name="getseconds"></a>COleDateTimeSpan::GetSeconds  
 擷取此日期/時間值的第二個部分。  
  
```
LONG GetSeconds() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 此日期/時間值的秒數部分。  
  
### <a name="remarks"></a>備註  
 傳回的值從-59 到 59 之間的這個函式範圍。  
  
 其他函式的查詢的值`COleDateTimeSpan`物件，請參閱下列的成員函式︰  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&19;](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_8.cpp)]  
  
##  <a name="a-namegetstatusa--coledatetimespangetstatus"></a><a name="getstatus"></a>COleDateTimeSpan::GetStatus  
 取得此狀態 （有效性）`COleDateTimeSpan`物件。  
  
```
DateTimeSpanStatus GetStatus() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 這個狀態`COleDateTimeSpan`值。  
  
### <a name="remarks"></a>備註  
 傳回值由定義**DateTimeSpanStatus**列舉型別，其中定義`COleDateTimeSpan`類別。  
  
 `enum DateTimeSpanStatus{`  
  
 `valid = 0,`  
  
 `invalid = 1,`  
  
 `null = 2,`  
  
 `};`  
  
 如需這些狀態值的簡短說明，請參閱下列清單︰  
  
- **COleDateTimeSpan::valid**指出此`COleDateTimeSpan`物件是否有效。  
  
- **COleDateTimeSpan::invalid**指出此`COleDateTimeSpan`物件無效; 也就是說，其值可能不正確。  
  
- **COleDateTimeSpan::null**指出此`COleDateTimeSpan`物件為 null，也就是此物件尚未提供任何值。 (這是 「 null 」 資料庫也就是 「 有沒有值時，"而不 c + + 的**NULL**。)  
  
 狀態`COleDateTimeSpan`物件無效在下列情況︰  
  
-   如果此物件發生溢位或反向溢位算術指派作業期間，也就是`+=`或`-=`。  
  
-   如果無效的值已指派給這個物件。  
  
-   如果此物件的狀態已明確設定為無效使用`SetStatus`。  
  
 如需可能的狀態設定為無效的作業的詳細資訊，請參閱[COleDateTimeSpan::operator +、-](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-)和[COleDateTimeSpan::operator + =、-=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq)。  
  
 如需有關界限`COleDateTimeSpan`值，請參閱文章[日期和時間︰ 自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)。  
  
##  <a name="a-namegettotaldaysa--coledatetimespangettotaldays"></a><a name="gettotaldays"></a>COleDateTimeSpan::GetTotalDays  
 擷取這個天數表示的日期/時間值。  
  
```
double GetTotalDays() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 以天數表示此日期/時間值。 雖然此函式的原型來傳回雙精度浮點數，它一律會傳回整數值。  
  
### <a name="remarks"></a>備註  
 此函式和之間的範圍大約 – 3.65e6 3.65e6 從傳回的值。  
  
 其他函式的查詢的值`COleDateTimeSpan`物件，請參閱下列的成員函式︰  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&20;](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_9.cpp)]  
  
##  <a name="a-namegettotalhoursa--coledatetimespangettotalhours"></a><a name="gettotalhours"></a>COleDateTimeSpan::GetTotalHours  
 擷取以小時為單位來表示此日期/時間值。  
  
```
double GetTotalHours() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 以小時為單位來表示此日期/時間值。 雖然此函式的原型來傳回雙精度浮點數，它一律會傳回整數值。  
  
### <a name="remarks"></a>備註  
 此函式和之間的範圍大約 – 8.77e7 8.77e7 從傳回的值。  
  
 其他函式的查詢的值`COleDateTimeSpan`物件，請參閱下列的成員函式︰  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>範例  
 請參閱範例[GetTotalDays](#gettotaldays)。  
  
##  <a name="a-namegettotalminutesa--coledatetimespangettotalminutes"></a><a name="gettotalminutes"></a>COleDateTimeSpan::GetTotalMinutes  
 擷取以分鐘為單位來表示此日期/時間值。  
  
```
double GetTotalMinutes() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 以分鐘為單位來表示此日期/時間值。 雖然此函式的原型來傳回雙精度浮點數，它一律會傳回整數值。  
  
### <a name="remarks"></a>備註  
 此函式和之間的範圍大約 – 5.26e9 5.26e9 從傳回的值。  
  
 其他函式的查詢的值`COleDateTimeSpan`物件，請參閱下列的成員函式︰  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>範例  
 請參閱範例[GetTotalDays](#gettotaldays)。  
  
##  <a name="a-namegettotalsecondsa--coledatetimespangettotalseconds"></a><a name="gettotalseconds"></a>COleDateTimeSpan::GetTotalSeconds  
 擷取以秒為單位來表示此日期/時間值。  
  
```
double GetTotalSeconds() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 以秒為單位來表示此日期/時間值。 雖然此函式的原型來傳回雙精度浮點數，它一律會傳回整數值。  
  
### <a name="remarks"></a>備註  
 此函式的傳回值介於大約 – 3.16e11 到 3.16e11。  
  
 其他函式的查詢的值`COleDateTimeSpan`物件，請參閱下列的成員函式︰  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
### <a name="example"></a>範例  
 請參閱範例[GetTotalDays](#gettotaldays)。  
  
##  <a name="a-namemspana--coledatetimespanmspan"></a><a name="m_span"></a>COleDateTimeSpan::m_span  
 基礎**雙**值`COleDateTime`物件。  
  
```
double m_span;
```  
  
### <a name="remarks"></a>備註  
 這個值表示的日期/時間範圍以天為單位。  
  
> [!CAUTION]
>  變更中的值**雙**資料成員會變更這個值`COleDateTimeSpan`物件。 不會變更這個狀態`COleDateTimeSpan`物件。  
  
##  <a name="a-namemstatusa--coledatetimespanmstatus"></a><a name="m_status"></a>COleDateTimeSpan::m_status  
 此資料成員的類型是列舉型別**DateTimeSpanStatus**，定義在`COleDateTimeSpan`類別。  
  
```
DateTimeSpanStatus m_status;
```  
  
### <a name="remarks"></a>備註  
 `enum DateTimeSpanStatus{`  
  
 `valid = 0,`  
  
 `invalid = 1,`  
  
 `null = 2,`  
  
 `};`  
  
 如需這些狀態值的簡短說明，請參閱下列清單︰  
  
- **COleDateTimeSpan::valid**指出此`COleDateTimeSpan`物件是否有效。  
  
- **COleDateTimeSpan::invalid**指出此`COleDateTimeSpan`物件無效; 也就是說，其值可能不正確。  
  
- **COleDateTimeSpan::null**指出此`COleDateTimeSpan`物件為 null，也就是此物件尚未提供任何值。 (這是 「 null 」 資料庫也就是 「 有沒有值時，"而不 c + + 的**NULL**。)  
  
 狀態`COleDateTimeSpan`物件無效在下列情況︰  
  
-   如果此物件發生溢位或反向溢位算術指派作業期間，也就是`+=`或`-=`。  
  
-   如果無效的值已指派給這個物件。  
  
-   如果此物件的狀態已明確設定為無效使用[SetStatus](#setstatus)。  
  
 如需可能的狀態設定為無效的作業的詳細資訊，請參閱[COleDateTimeSpan::operator +、-](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-)和[COleDateTimeSpan::operator + =、-=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq)。  
  
> [!CAUTION]
>  此資料成員是進階程式設計的情況下。 您應該使用內嵌成員函式[GetStatus](#getstatus)和[SetStatus](#setstatus)。 請參閱`SetStatus`的其他注意事項，關於明確設定此資料成員。  
  
 如需有關界限`COleDateTimeSpan`值，請參閱文章[日期和時間︰ 自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)。  
  
##  <a name="a-nameoperatoreqa--coledatetimespanoperator-"></a><a name="operator_eq"></a>COleDateTimeSpan::operator =  
 複製`COleDateTimeSpan`值。  
  
```
COleDateTimeSpan& operator=(double dblSpanSrc) throw();
```  
  
### <a name="remarks"></a>備註  
 這個多載的指派運算子會將來源的日期/時間範圍值複製到這`COleDateTimeSpan`物件。  
  
##  <a name="a-nameoperatoradd-a--coledatetimespanoperator---"></a><a name="operator_add_-"></a>COleDateTimeSpan::operator +、-  
 新增、 相減，以及變更符號`COleDateTimeSpan`值。  
  
```
COleDateTimeSpan operator+(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-() const throw();
```  
  
### <a name="remarks"></a>備註  
 前兩個運算子可讓您加入和減去的日期/時間值。 第三個可讓您變更日期/時間值的正負號。  
  
 如果任一個運算元是 null，產生的狀態`COleDateTimeSpan`值為 null。  
  
 如果任一個運算元無效，而且其他不是 null，產生的狀態`COleDateTimeSpan`值無效。  
  
 如需有關有效且不正確，並為 null 的狀態值的詳細資訊，請參閱[m_status](#m_status)成員變數。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&23;](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_10.cpp)]  
  
##  <a name="a-nameoperatoraddeq-eqa--coledatetimespanoperator---"></a><a name="operator_add_eq_-_eq"></a>COleDateTimeSpan::operator + =、 =  
 加號和減號運算子`COleDateTimeSpan`值從這個`COleDateTimeSpan`值。  
  
```
COleDateTimeSpan& operator+=(const COleDateTimeSpan dateSpan) throw();
COleDateTimeSpan& operator-=(const COleDateTimeSpan dateSpan) throw();
```  
  
### <a name="remarks"></a>備註  
 這些運算子可讓您加入和減去的日期/時間值從這個`COleDateTimeSpan`物件。 如果任一個運算元是 null，產生的狀態`COleDateTimeSpan`值為 null。  
  
 如果任一個運算元無效，而且其他不是 null，產生的狀態`COleDateTimeSpan`值無效。  
  
 如需有關有效且不正確，並為 null 的狀態值的詳細資訊，請參閱[m_status](#m_status)成員變數。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&24;](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_11.cpp)]  
  
##  <a name="a-nameoperatordoublea--coledatetimespanoperator-double"></a><a name="operator_double"></a>COleDateTimeSpan::operator double  
 此轉換`COleDateTimeSpan`值**雙**。  
  
```
operator double() const throw();
```  
  
### <a name="remarks"></a>備註  
 這個運算子會傳回這個值`COleDateTimeSpan`天浮點數的值。  
  
##  <a name="a-namesetdatetimespana--coledatetimespansetdatetimespan"></a><a name="setdatetimespan"></a>COleDateTimeSpan::SetDateTimeSpan  
 設定此日期/時間值的值。  
  
```
void SetDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```  
  
### <a name="parameters"></a>參數  
 `lDays`, `nHours`, `nMins`, `nSecs`  
 表示的日期範圍和時間範圍值複製到這`COleDateTimeSpan`物件。  
  
### <a name="remarks"></a>備註  
 查詢的值的函式的`COleDateTimeSpan`物件，請參閱下列的成員函式︰  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&21;](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_12.cpp)]  
  
##  <a name="a-namesetstatusa--coledatetimespansetstatus"></a><a name="setstatus"></a>COleDateTimeSpan::SetStatus  
 設定狀態 （有效性） 這個`COleDateTimeSpan`物件。  
  
```
void SetStatus(DateTimeSpanStatus status) throw();
```  
  
### <a name="parameters"></a>參數  
 *status*  
 這個新的狀態值`COleDateTimeSpan`物件。  
  
### <a name="remarks"></a>備註  
 *狀態*參數值由定義**DateTimeSpanStatus**列舉型別，其中定義`COleDateTimeSpan`類別。  
  
 `enum DateTimeSpanStatus{`  
  
 `valid = 0,`  
  
 `invalid = 1,`  
  
 `null = 2,`  
  
 `};`  
  
 如需這些狀態值的簡短說明，請參閱下列清單︰  
  
- **COleDateTimeSpan::valid**指出此`COleDateTimeSpan`物件是否有效。  
  
- **COleDateTimeSpan::invalid**指出此`COleDateTimeSpan`物件無效; 也就是說，其值可能不正確。  
  
- **COleDateTimeSpan::null**指出此`COleDateTimeSpan`物件為 null，也就是此物件尚未提供任何值。 (這是 「 null 」 資料庫也就是 「 有沒有值時，"而不 c + + 的**NULL**。)  
  
    > [!CAUTION]
    >  這個函數是進階程式設計的情況。 此函式不會更改此物件中的資料。 它將最常使用的狀態設為`null`或**無效**。 請注意，指派運算子 ([運算子 =](#eq)) 和[SetDateTimeSpan](#setdatetimespan)沒有設定物件的來源值為基礎的狀態。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&22;](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_13.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [COleDateTime 類別](../../atl-mfc-shared/reference/coledatetime-class.md)   
 [CTime 類別](../../atl-mfc-shared/reference/ctime-class.md)   
 [CTimeSpan 類別](../../atl-mfc-shared/reference/ctimespan-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)




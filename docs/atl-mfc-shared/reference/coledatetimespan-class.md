---
title: "COleDateTimeSpan 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::Format
- ATLCOMTIME/ATL::COleDateTimeSpan::GetDays
- ATLCOMTIME/ATL::COleDateTimeSpan::GetHours
- ATLCOMTIME/ATL::COleDateTimeSpan::GetMinutes
- ATLCOMTIME/ATL::COleDateTimeSpan::GetSeconds
- ATLCOMTIME/ATL::COleDateTimeSpan::GetStatus
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalDays
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalHours
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalMinutes
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalSeconds
- ATLCOMTIME/ATL::COleDateTimeSpan::SetDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::SetStatus
- ATLCOMTIME/ATL::COleDateTimeSpan::m_span
- ATLCOMTIME/ATL::COleDateTimeSpan::m_status
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 0c696f59a6f4be7b4d966aad2a16a846d737009f
ms.contentlocale: zh-tw
ms.lasthandoff: 04/04/2017

---
# <a name="coledatetimespan-class"></a>COleDateTimeSpan 類別
代表相對時間、 時間範圍。  
  
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
|[COleDateTimeSpan::GetDays](#getdays)|傳回此範圍的日期部分`COleDateTimeSpan`物件表示。|  
|[COleDateTimeSpan::GetHours](#gethours)|傳回此範圍的小時部分`COleDateTimeSpan`物件表示。|  
|[COleDateTimeSpan::GetMinutes](#getminutes)|這會傳回的分鐘部分之範圍`COleDateTimeSpan`物件表示。|  
|[COleDateTimeSpan::GetSeconds](#getseconds)|傳回此範圍的第二個部分`COleDateTimeSpan`物件表示。|  
|[COleDateTimeSpan::GetStatus](#getstatus)|取得這個狀態 （有效性）`COleDateTimeSpan`物件。|  
|[COleDateTimeSpan::GetTotalDays](#gettotaldays)|傳回此天數`COleDateTimeSpan`物件表示。|  
|[COleDateTimeSpan::GetTotalHours](#gettotalhours)|這會傳回的時數`COleDateTimeSpan`物件表示。|  
|[COleDateTimeSpan::GetTotalMinutes](#gettotalminutes)|傳回此分鐘數`COleDateTimeSpan`物件表示。|  
|[COleDateTimeSpan::GetTotalSeconds](#gettotalseconds)|傳回此秒數`COleDateTimeSpan`物件表示。|  
|[COleDateTimeSpan::SetDateTimeSpan](#setdatetimespan)|設定這個值`COleDateTimeSpan`物件。|  
|[COleDateTimeSpan::SetStatus](#setstatus)|設定這個狀態 （有效性）`COleDateTimeSpan`物件。|  
  
### <a name="public-operators"></a>公用運算子  
  
|||  
|-|-|  
|[運算子 +、-](#operator_add_-)|加入、 subtract、 和變更符號`COleDateTimeSpan`值。|  
|[運算子 + =、-= 左邊](#operator_add_eq_-_eq)|加號和減號運算子`COleDateTimeSpan`值從此`COleDateTimeSpan`值。|  
|[運算子 =](#operator_eq)|複製`COleDateTimeSpan`值。|  
|[運算子 = =、<,></,><>](#coledatetimespan_relational_operators)|比較兩個`COleDateTimeSpan`值。|  
|[運算子 double](#operator_double)|這會將轉換`COleDateTimeSpan`值設定為**double**。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[COleDateTimeSpan::m_span](#m_span)|包含基礎**double**這個`COleDateTimeSpan`物件。|  
|[COleDateTimeSpan::m_status](#m_status)|包含的狀態`COleDateTimeSpan`物件。|  
  
## <a name="remarks"></a>備註  
 `COleDateTimeSpan`沒有基底類別。  
  
 A`COleDateTimeSpan`持續時間，以天為單位。  
  
 `COleDateTimeSpan`使用其附屬類別[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)。 `COleDateTime`封裝**日期**OLE automation 資料類型。 `COleDateTime`表示絕對時間值。 所有`COleDateTime`計算涉及`COleDateTimeSpan`值。 這些類別之間的關聯性是類似於間[CTime](../../atl-mfc-shared/reference/ctime-class.md)和[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)。  
  
 如需有關`COleDateTime`和`COleDateTimeSpan`類別，請參閱文章[日期和時間︰ 自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)。  
  
## <a name="requirements"></a>需求  
 **標頭︰** ATLComTime.h  
  
##  <a name="coledatetimespan_relational_operators"></a>COleDateTimeSpan 關係運算子  
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
>  如果任一個運算元無效，會發生 ATLASSERT。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities # 25](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_1.cpp)]  
  
 [!code-cpp[NVC_ATLMFC_Utilities # 26](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_2.cpp)]  
  
##  <a name="coledatetimespan"></a>COleDateTimeSpan::COleDateTimeSpan  
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
 所有這些建構函式建立新`COleDateTimeSpan`物件初始化為指定的值。 每個這些建構函式的簡短描述如下︰  
  
- **COleDateTimeSpan （)**建構`COleDateTimeSpan`物件初始化為 0。  
  
- **COleDateTimeSpan (** `dblSpanSrc` **)**建構`COleDateTimeSpan`從浮點值的物件。  
  
- **COleDateTimeSpan (** `lDays` **，** `nHours` **，** `nMins` **，** `nSecs` **)**建構`COleDateTimeSpan`物件初始化為指定的數值。  
  
 新的狀態`COleDateTimeSpan`物件設定為有效。  
  
 如需有關的界限`COleDateTimeSpan`值，請參閱文章[日期和時間︰ 自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities # 14](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_3.cpp)]  
  
##  <a name="format"></a>COleDateTimeSpan::Format  
 產生的格式化的字串表示`COleDateTimeSpan`物件。  
  
```
CString Format(LPCTSTR pFormat) const;
CString Format(UINT nID) const;
```  
  
### <a name="parameters"></a>參數  
 `pFormat`  
 格式字串類似於`printf`格式化字串。 格式化程式碼，加上百分比 ( `%`) 登入，對應會取代`COleDateTimeSpan`元件。 格式字串中的其他字元都會複製到傳回的字串不變。 值和的格式化程式碼的意義**格式**如下所示︰  
  
- **%H**當天的時數  
  
- **%M**分鐘在目前的小時  
  
- **%S**中目前的分鐘數的秒數  
  
- **%%**百分比符號  
  
 四個以上所列的格式化程式碼是可接受格式的唯一代碼。  
  
-  
  
 `nID`  
 格式控制字串資源識別碼。  
  
### <a name="return-value"></a>傳回值  
 A `CString` ，其中包含已格式化的日期/時間值。  
  
### <a name="remarks"></a>備註  
 呼叫這些函式來建立格式化的表示法的時間範圍值。 如果這個狀態`COleDateTimeSpan`物件為 null，傳回的值為空字串。 如果狀態不正確，則傳回字串指定字串資源**IDS_INVALID_DATETIMESPAN**。  
  
 此函式之表單的簡短描述如下︰  
  
 **Format(** `pFormat` **)**  
 此表單會使用格式字串，其中包含特殊格式的程式碼會加上百分比符號 （%），將值格式化中`printf`。 格式化字串會當做參數傳遞至函式。  
  
 **Format(** `nID` **)**  
 此表單會使用格式字串，其中包含特殊格式的程式碼會加上百分比符號 （%），將值格式化中`printf`。 格式化字串則為資源。 此字串資源的識別碼會當做參數傳遞。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities # 15](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_4.cpp)]  
  
##  <a name="getdays"></a>COleDateTimeSpan::GetDays  
 擷取這個日期/時間值的日期部分。  
  
```
LONG GetDays() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 此日期/時間值的日數部分。  
  
### <a name="remarks"></a>備註  
 傳回從數值之間的這個函式範圍大約-3,615,000 和 3,615,000。  
  
 對查詢的值的其他函式`COleDateTimeSpan`物件，請參閱下列成員函式︰  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities # 16](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_5.cpp)]  
  
##  <a name="gethours"></a>COleDateTimeSpan::GetHours  
 擷取這個日期/時間值的小時部分。  
  
```
LONG GetHours() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 此日期/時間值的小時部分。  
  
### <a name="remarks"></a>備註  
 傳回介於-23 到 23 之間的這個函式範圍的值。  
  
 對查詢的值的其他函式`COleDateTimeSpan`物件，請參閱下列成員函式︰  
  
- [GetDays](#getdays)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities # 17](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_6.cpp)]  
  
##  <a name="getminutes"></a>COleDateTimeSpan::GetMinutes  
 擷取這個日期/時間值的分鐘部分。  
  
```
LONG GetMinutes() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 此日期/時間值的分鐘部分。  
  
### <a name="remarks"></a>備註  
 傳回介於-59 到 59 之間的這個函式範圍的值。  
  
 對查詢的值的其他函式`COleDateTimeSpan`物件，請參閱下列成員函式︰  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities # 18](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_7.cpp)]  
  
##  <a name="getseconds"></a>COleDateTimeSpan::GetSeconds  
 擷取這個日期/時間值的第二個部分。  
  
```
LONG GetSeconds() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 此日期/時間值的秒數部分。  
  
### <a name="remarks"></a>備註  
 傳回介於-59 到 59 之間的這個函式範圍的值。  
  
 對查詢的值的其他函式`COleDateTimeSpan`物件，請參閱下列成員函式︰  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities # 19](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_8.cpp)]  
  
##  <a name="getstatus"></a>COleDateTimeSpan::GetStatus  
 取得這個狀態 （有效性）`COleDateTimeSpan`物件。  
  
```
DateTimeSpanStatus GetStatus() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 這個狀態`COleDateTimeSpan`值。  
  
### <a name="remarks"></a>備註  
 傳回值由定義**DateTimeSpanStatus**列舉型別，其中定義`COleDateTimeSpan`類別。  
  
```  
enum DateTimeSpanStatus{  
   valid = 0,  
   invalid = 1,  
   null = 2,  
};  
```  
  
 如需這些狀態值的簡短說明，請參閱下列清單︰  
  
- **COleDateTimeSpan::valid**指出此`COleDateTimeSpan`物件是否有效。  
  
- **COleDateTimeSpan::invalid**指出此`COleDateTimeSpan`物件無效; 也就是說，其值可能不正確。  
  
- **COleDateTimeSpan::null**指出此`COleDateTimeSpan`物件為 null，也就是已針對此物件提供任何值。 (這是 「 null 」 中的"having 沒有值時，"而不 c + + 資料庫意義**NULL**。)  
  
 狀態`COleDateTimeSpan`物件不能用在下列情況︰  
  
-   如果此物件發生溢位或反向溢位算術指派作業期間，也就是`+=`或`-=`。  
  
-   如果無效的值已指派給這個物件。  
  
-   如果此物件的狀態已明確設定為無效的使用`SetStatus`。  
  
 如需可能會將狀態設為無效的作業的詳細資訊，請參閱[COleDateTimeSpan::operator +、-](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-)和[COleDateTimeSpan::operator + =、-=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq)。  
  
 如需有關的界限`COleDateTimeSpan`值，請參閱文章[日期和時間︰ 自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)。  
  
##  <a name="gettotaldays"></a>COleDateTimeSpan::GetTotalDays  
 擷取這個天數表示的日期/時間值。  
  
```
double GetTotalDays() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 以天數表示此日期/時間值。 此函式是原型才能傳回 double 值，雖然它一定會傳回整數值。  
  
### <a name="remarks"></a>備註  
 此函式和之間的範圍大約-3.65e6 3.65e6 從傳回的值。  
  
 對查詢的值的其他函式`COleDateTimeSpan`物件，請參閱下列成員函式︰  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities # 20](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_9.cpp)]  
  
##  <a name="gettotalhours"></a>COleDateTimeSpan::GetTotalHours  
 擷取以小時為單位來表示此日期/時間值。  
  
```
double GetTotalHours() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 以小時表示此日期/時間值。 此函式是原型才能傳回 double 值，雖然它一定會傳回整數值。  
  
### <a name="remarks"></a>備註  
 此函式和之間的範圍大約-8.77e7 8.77e7 從傳回的值。  
  
 對查詢的值的其他函式`COleDateTimeSpan`物件，請參閱下列成員函式︰  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>範例  
 請參閱範例的[GetTotalDays](#gettotaldays)。  
  
##  <a name="gettotalminutes"></a>COleDateTimeSpan::GetTotalMinutes  
 擷取以分鐘為單位來表示此日期/時間值。  
  
```
double GetTotalMinutes() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 以分鐘為單位來表示此日期/時間值。 此函式是原型才能傳回 double 值，雖然它一定會傳回整數值。  
  
### <a name="remarks"></a>備註  
 此函式和之間的範圍大約-5.26e9 5.26e9 從傳回的值。  
  
 對查詢的值的其他函式`COleDateTimeSpan`物件，請參閱下列成員函式︰  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>範例  
 請參閱範例的[GetTotalDays](#gettotaldays)。  
  
##  <a name="gettotalseconds"></a>COleDateTimeSpan::GetTotalSeconds  
 擷取以秒為單位來表示此日期/時間值。  
  
```
double GetTotalSeconds() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 以秒為單位來表示此日期/時間值。 此函式是原型才能傳回 double 值，雖然它一定會傳回整數值。  
  
### <a name="remarks"></a>備註  
 此函式的傳回值的範圍之間大約-3.16e11 至 3.16e11。  
  
 對查詢的值的其他函式`COleDateTimeSpan`物件，請參閱下列成員函式︰  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
### <a name="example"></a>範例  
 請參閱範例的[GetTotalDays](#gettotaldays)。  
  
##  <a name="m_span"></a>COleDateTimeSpan::m_span  
 基礎**double**值，這個`COleDateTime`物件。  
  
```
double m_span;
```  
  
### <a name="remarks"></a>備註  
 這個值表示的日期/時間範圍以天為單位。  
  
> [!CAUTION]
>  變更中的值**double**資料成員將會變更這個值`COleDateTimeSpan`物件。 不會變更這個狀態`COleDateTimeSpan`物件。  
  
##  <a name="m_status"></a>COleDateTimeSpan::m_status  
 此資料成員的類型是列舉型別**DateTimeSpanStatus**，定義內`COleDateTimeSpan`類別。  
  
```
DateTimeSpanStatus m_status;
```  
  
### <a name="remarks"></a>備註  
  
```  
enum DateTimeSpanStatus{  
   valid = 0,  
   invalid = 1,  
   null = 2,  
   };  
```  
  
 如需這些狀態值的簡短說明，請參閱下列清單︰  
  
- **COleDateTimeSpan::valid**指出此`COleDateTimeSpan`物件是否有效。  
  
- **COleDateTimeSpan::invalid**指出此`COleDateTimeSpan`物件無效; 也就是說，其值可能不正確。  
  
- **COleDateTimeSpan::null**指出此`COleDateTimeSpan`物件為 null，也就是已針對此物件提供任何值。 (這是 「 null 」 中的"having 沒有值時，"而不 c + + 資料庫意義**NULL**。)  
  
 狀態`COleDateTimeSpan`物件不能用在下列情況︰  
  
-   如果此物件發生溢位或反向溢位算術指派作業期間，也就是`+=`或`-=`。  
  
-   如果無效的值已指派給這個物件。  
  
-   如果此物件的狀態已明確設定為無效的使用[SetStatus](#setstatus)。  
  
 如需可能會將狀態設為無效的作業的詳細資訊，請參閱[COleDateTimeSpan::operator +、-](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-)和[COleDateTimeSpan::operator + =、-=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq)。  
  
> [!CAUTION]
>  此資料成員是針對進階程式的情況。 您應該使用內嵌成員函式[GetStatus](#getstatus)和[SetStatus](#setstatus)。 請參閱`SetStatus`的其他注意事項，關於明確設定此資料成員。  
  
 如需有關的界限`COleDateTimeSpan`值，請參閱文章[日期和時間︰ 自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)。  
  
##  <a name="operator_eq"></a>COleDateTimeSpan::operator =  
 複製`COleDateTimeSpan`值。  
  
```
COleDateTimeSpan& operator=(double dblSpanSrc) throw();
```  
  
### <a name="remarks"></a>備註  
 此多載的指派運算子複製到這個來源的日期/時間值`COleDateTimeSpan`物件。  
  
##  <a name="operator_add_-"></a>COleDateTimeSpan::operator +、-  
 加入、 subtract、 和變更符號`COleDateTimeSpan`值。  
  
```
COleDateTimeSpan operator+(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-() const throw();
```  
  
### <a name="remarks"></a>備註  
 前兩個運算子可讓您加入和減去的日期/時間值。 第三個可讓您變更日期/時間值的正負號。  
  
 如果其中一個運算元為 null，產生的狀態`COleDateTimeSpan`值為 null。  
  
 如果任一運算元無效，而且其他不是 null，產生的狀態`COleDateTimeSpan`值無效。  
  
 如需有關有效、 無效的 null 狀態值的詳細資訊，請參閱[m_status](#m_status)成員變數。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities # 23](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_10.cpp)]  
  
##  <a name="operator_add_eq_-_eq"></a>COleDateTimeSpan::operator + =、-= 左邊  
 加號和減號運算子`COleDateTimeSpan`值從此`COleDateTimeSpan`值。  
  
```
COleDateTimeSpan& operator+=(const COleDateTimeSpan dateSpan) throw();
COleDateTimeSpan& operator-=(const COleDateTimeSpan dateSpan) throw();
```  
  
### <a name="remarks"></a>備註  
 這些運算子可讓您加入和減去的日期/時間值從這個`COleDateTimeSpan`物件。 如果其中一個運算元為 null，產生的狀態`COleDateTimeSpan`值為 null。  
  
 如果任一運算元無效，而且其他不是 null，產生的狀態`COleDateTimeSpan`值無效。  
  
 如需有關有效、 無效的 null 狀態值的詳細資訊，請參閱[m_status](#m_status)成員變數。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities # 24](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_11.cpp)]  
  
##  <a name="operator_double"></a>COleDateTimeSpan::operator double  
 這會將轉換`COleDateTimeSpan`值設定為**double**。  
  
```
operator double() const throw();
```  
  
### <a name="remarks"></a>備註  
 這個運算子會傳回這個值`COleDateTimeSpan`天浮點數的值。  
  
##  <a name="setdatetimespan"></a>COleDateTimeSpan::SetDateTimeSpan  
 設定此日期/時間值的值。  
  
```
void SetDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```  
  
### <a name="parameters"></a>參數  
 `lDays`, `nHours`, `nMins`, `nSecs`  
 表示的日期範圍與時間範圍值複製到這個`COleDateTimeSpan`物件。  
  
### <a name="remarks"></a>備註  
 查詢的值的函式`COleDateTimeSpan`物件，請參閱下列成員函式︰  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities # 21](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_12.cpp)]  
  
##  <a name="setstatus"></a>COleDateTimeSpan::SetStatus  
 設定這個狀態 （有效性）`COleDateTimeSpan`物件。  
  
```
void SetStatus(DateTimeSpanStatus status) throw();
```  
  
### <a name="parameters"></a>參數  
 *status*  
 這個新的狀態值`COleDateTimeSpan`物件。  
  
### <a name="remarks"></a>備註  
 *狀態*參數值由定義**DateTimeSpanStatus**列舉型別，其中定義`COleDateTimeSpan`類別。  
  
```  
enum DateTimeSpanStatus{  
   valid = 0,  
   invalid = 1,  
   null = 2,  
   };  
```  
  
 如需這些狀態值的簡短說明，請參閱下列清單︰  
  
- **COleDateTimeSpan::valid**指出此`COleDateTimeSpan`物件是否有效。  
  
- **COleDateTimeSpan::invalid**指出此`COleDateTimeSpan`物件無效; 也就是說，其值可能不正確。  
  
- **COleDateTimeSpan::null**指出此`COleDateTimeSpan`物件為 null，也就是已針對此物件提供任何值。 (這是 「 null 」 中的"having 沒有值時，"而不 c + + 資料庫意義**NULL**。)  
  
    > [!CAUTION]
    >  此函式是針對進階程式的情況。 此函式不會改變此物件中的資料。 它會最常使用的狀態設為`null`或**無效**。 請注意，指派運算子 ([運算子 =](#eq)) 和[SetDateTimeSpan](#setdatetimespan)要設定物件的來源值為基礎的狀態。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities # 22](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_13.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [COleDateTime 類別](../../atl-mfc-shared/reference/coledatetime-class.md)   
 [CTime 類別](../../atl-mfc-shared/reference/ctime-class.md)   
 [CTimeSpan 類別](../../atl-mfc-shared/reference/ctimespan-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)




---
title: "CComCurrency 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComCurrency
- ATL.CComCurrency
- ATL::CComCurrency
dev_langs:
- C++
helpviewer_keywords:
- CComCurrency class
ms.assetid: a1c3d10a-bba6-40cc-8bcf-aed9023c8a9e
caps.latest.revision: 21
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
ms.openlocfilehash: 1b0b4fa5f42bd060b08ef90d09eee8d9d2d76fe6
ms.lasthandoff: 02/24/2017

---
# <a name="ccomcurrency-class"></a>CComCurrency 類別
`CComCurrency` 有方法和運算子可建立及管理 CURRENCY 物件。  
  
## <a name="syntax"></a>語法  
  
```
class CComCurrency
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CComCurrency::CComCurrency](#ccomcurrency)|`CComCurrency` 物件的建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CComCurrency::GetCurrencyPtr](#getcurrencyptr)|傳回 `m_currency` 資料成員的位址。|  
|[CComCurrency::GetFraction](#getfraction)|呼叫此方法以傳回 `CComCurrency` 物件的小數部分。|  
|[CComCurrency::GetInteger](#getinteger)|呼叫此方法以傳回 `CComCurrency` 物件的整數部分。|  
|[CComCurrency::Round](#round)|呼叫此方法將 `CComCurrency` 物件四捨五入到最接近的整數值。|  
|[CComCurrency::SetFraction](#setfraction)|呼叫此方法以設定 `CComCurrency` 物件的小數部分。|  
|[CComCurrency::SetInteger](#setinteger)|呼叫此方法以設定 `CComCurrency` 物件的整數部分。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CComCurrency::operator-](#operator_-)|此運算子用在 `CComCurrency` 物件上執行減法。|  
|[CComCurrency::operator ！ =](#operator_neq)|比較兩個 `CComCurrency` 物件是否不相等。|  
|[CComCurrency::operator *](#operator_star)|此運算子用在 `CComCurrency` 物件上執行乘法。|  
|[CComCurrency::operator * =](#operator_star_eq)|此運算子用在 `CComCurrency` 物件上執行乘法並指派結果。|  
|[CComCurrency::operator /](#operator_div)|此運算子用在 `CComCurrency` 物件上執行除法。|  
|[CComCurrency::operator / =](#operator_div_eq)|此運算子用在 `CComCurrency` 物件上執行除法並指派結果。|  
|[CComCurrency::operator +](#operator_add)|此運算子用在 `CComCurrency` 物件上執行加法。|  
|[CComCurrency::operator + =](#operator_add_eq)|此運算子用在 `CComCurrency` 物件上執行加法並指派結果給目前物件。|  
|[CComCurrency::operator](#operator_lt)|此運算子比較兩個 `CComCurrency` 物件來判斷何者較小。|  
|[CComCurrency::operator<>](#operator_lt_eq)|此運算子比較兩個 `CComCurrency` 物件來判斷是否相等或何者較小。|  
|[CComCurrency::operator =](#operator_eq)|此運算子將 `CComCurrency` 物件指派給新的值。|  
|[CComCurrency::operator =](#operator_-_eq)|此運算子用在 `CComCurrency` 物件上執行減法並指派結果。|  
|[CComCurrency::operator = =](#operator_eq_eq)|此運算子比較兩個 `CComCurrency` 物件是否相等。|  
|[CComCurrency::operator >](#operator_gt)|此運算子比較兩個 `CComCurrency` 物件來判斷何者較大。|  
|[CComCurrency::operator > =](#operator_gt_eq)|此運算子比較兩個 `CComCurrency` 物件來判斷是否相等或何者較大。|  
|[CComCurrency::operator 貨幣](#operator_currency)|轉換 `CURRENCY` 物件。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CComCurrency::m_currency](#m_currency)|您的類別執行個體建立的 `CURRENCY` 變數。|  
  
## <a name="remarks"></a>備註  
 `CComCurrency`是的包裝函式**貨幣**資料型別。 **貨幣**實作為以 10000 倍的 8 位元二補數整數值。 這得出一個定點數字，小數點左邊 15 位數，小數點右邊 4 位數。 **貨幣**資料類型是非常有用，計算涉及金錢，或任何定點計算精確度，都很重要。  
  
 **CComCurrency**包裝函式會實作此定點類型的算術、 指派及比較作業。 已選取支援的應用程式來控制固定點計算期間可能發生的四捨五入錯誤。  
  
 `CComCurrency` 物件讓您分兩部分來存取小數點兩側的數字：整數部分儲存小數點左邊的值，小數部分儲存小數點右邊的值。 -9999 之間的整數值在內部儲存的小數部分 ( **CY_MIN_FRACTION**) 和 +9999 ( **CY_MAX_FRACTION**)。 此方法[CComCurrency::GetFraction](#getfraction)傳回值，這個值以 10000 倍倍 ( **CY_SCALE**)。  
  
 指定的整數和小數的元件時**CComCurrency**物件時，請記得的小數部分是範圍 0 到 9999 之間的數字。 在處理貨幣時，例如，美元在小數點後面只以兩個有效位數來表示金額，這就很重要。 即使沒有顯示最後兩位數，也必須納入考量。  
  
|值|可能的 CComCurrency 指派|  
|-----------|---------------------------------------|  
|$10.50|CComCurrency(10,5000)*或*CComCurrency(10.50)|  
|$10.05|CComCurrency(10,500)*或*CComCurrency(10.05)|  
  
 值**CY_MIN_FRACTION**， **CY_MAX_FRACTION**，和**CY_SCALE** atlcur.h 中所定義。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlcur.h  
  
##  <a name="a-nameccomcurrencya--ccomcurrencyccomcurrency"></a><a name="ccomcurrency"></a>CComCurrency::CComCurrency  
 建構函式。  
  
```
CComCurrency() throw();
CComCurrency(const CComCurrency& curSrc) throw();
CComCurrency(CURRENCY cySrc) throw();
CComCurrency(DECIMAL dSrc);
CComCurrency(ULONG ulSrc);  
CComCurrency(USHORT usSrc);  
CComCurrency(CHAR cSrc);  
CComCurrency(DOUBLE dSrc);  
CComCurrency(FLOAT fSrc);  
CComCurrency(LONG lSrc);  
CComCurrency(SHORT sSrc);  
CComCurrency(BYTE bSrc);  
CComCurrency(LONGLONG nInteger, SHORT nFraction);  
explicit CComCurrency(LPDISPATCH pDispSrc);  
explicit CComCurrency(const VARIANT& varSrc);  
explicit CComCurrency(LPCWSTR szSrc);  
explicit CComCurrency(LPCSTR szSrc);
```  
  
### <a name="parameters"></a>參數  
 `curSrc`  
 現有的 `CComCurrency` 物件。  
  
 `cySrc`  
 型別的變數**貨幣**。  
  
 `bSrc`, `dSrc`, `fSrc`, `lSrc`, *sSrc*, *ulSrc, usSrc*  
 提供給成員變數的初始值`m_currency`。  
  
 `cSrc`  
 包含提供給成員變數的起始值的字元`m_currency`。  
  
 `nInteger`*nFraction*  
 整數和分數元件的初始的貨幣值。 請參閱[CComCurrency](../../atl/reference/ccomcurrency-class.md)概觀如需詳細資訊。  
  
 `pDispSrc`  
 `IDispatch`指標。  
  
 *varSrc*  
 型別的變數**VARIANT**。 目前執行緒的地區設定用來執行轉換。  
  
 `szSrc`  
 Unicode 或 ANSI 字串，包含起始值。 目前執行緒的地區設定用來執行轉換。  
  
### <a name="remarks"></a>備註  
 建構函式設定初始值[CComCurrency::m_currency](#m_currency)，並接受各種不同的資料類型，包括整數、 字串、 浮點數，**貨幣**變數，以及其他`CComCurrency`物件。 如果未不提供任何值，`m_currency`設為 0。  
  
 如果發生錯誤，例如溢位，而沒有空白的例外狀況規格的建構函式 ( **throw （)**) 呼叫`AtlThrow`，描述錯誤的 HRESULT。  
  
 使用浮點數或雙精度浮點值時指派的值，請注意， **CComCurrency(10.50)**相當於**CComCurrency(10,5000)**而非**CComCurrency(10,50)**。  
  
##  <a name="a-namegetcurrencyptra--ccomcurrencygetcurrencyptr"></a><a name="getcurrencyptr"></a>CComCurrency::GetCurrencyPtr  
 傳回 `m_currency` 資料成員的位址。  
  
```
CURRENCY* GetCurrencyPtr() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的位址`m_currency`資料成員  
  
##  <a name="a-namegetfractiona--ccomcurrencygetfraction"></a><a name="getfraction"></a>CComCurrency::GetFraction  
 呼叫這個方法傳回的小數部分`CComCurrency`物件。  
  
```
SHORT GetFraction() const;
```  
  
### <a name="return-value"></a>傳回值  
 傳回的小數部分`m_currency`資料成員。  
  
### <a name="remarks"></a>備註  
 小數部分是 4 位元整數之間的值-9999 ( **CY_MIN_FRACTION**) 和 +9999 ( **CY_MAX_FRACTION**)。 `GetFraction`傳回此值以 10000 倍 ( **CY_SCALE**)。 值**CY_MIN_FRACTION**， **CY_MAX_FRACTION**，和**CY_SCALE** atlcur.h 中所定義。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&50;](../../atl/codesnippet/cpp/ccomcurrency-class_1.cpp)]  
  
##  <a name="a-namegetintegera--ccomcurrencygetinteger"></a><a name="getinteger"></a>CComCurrency::GetInteger  
 呼叫此方法來取得整數部分`CComCurrency`物件。  
  
```
LONGLONG GetInteger() const;
```  
  
### <a name="return-value"></a>傳回值  
 傳回的整數部份`m_currency`資料成員。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&51;](../../atl/codesnippet/cpp/ccomcurrency-class_2.cpp)]  
  
##  <a name="a-namemcurrencya--ccomcurrencymcurrency"></a><a name="m_currency"></a>CComCurrency::m_currency  
 **貨幣**資料成員。  
  
```
CURRENCY m_currency;
```  
  
### <a name="remarks"></a>備註  
 這個成員會保存貨幣存取和操作這個類別的方法。  
  
##  <a name="a-nameoperator-a--ccomcurrencyoperator--"></a><a name="operator_-"></a>CComCurrency::operator-  
 此運算子用在 `CComCurrency` 物件上執行減法。  
  
```
CComCurrency operator-() const;
CComCurrency operator-(const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>參數  
 `cur`  
 `CComCurrency` 物件。  
  
### <a name="return-value"></a>傳回值  
 傳回`CComCurrency`物件，代表減法運算的結果。 如果發生錯誤，例如溢位，此運算子會呼叫`AtlThrow`，描述錯誤的 HRESULT。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&55;](../../atl/codesnippet/cpp/ccomcurrency-class_3.cpp)]  
  
##  <a name="a-nameoperatorneqa--ccomcurrencyoperator-"></a><a name="operator_neq"></a>CComCurrency::operator ！ =  
 這個運算子比較兩個物件不相等。  
  
```
bool operator!= (const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>參數  
 `cur`  
 要比較的 `CComCurrency` 物件。  
  
### <a name="return-value"></a>傳回值  
 傳回**true**要比較的項目是否不等於`CComCurrency`物件; 否則**false**。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&56;](../../atl/codesnippet/cpp/ccomcurrency-class_4.cpp)]  
  
##  <a name="a-nameoperatorstara--ccomcurrencyoperator-"></a><a name="operator_star"></a>CComCurrency::operator *  
 此運算子用在 `CComCurrency` 物件上執行乘法。  
  
```
CComCurrency operator*(long nOperand) const;
CComCurrency operator*(const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>參數  
 `nOperand`  
 乘數。  
  
 `cur`  
 `CComCurrency`物件做為乘數。  
  
### <a name="return-value"></a>傳回值  
 傳回`CComCurrency`物件，代表相乘的結果。 如果發生錯誤，例如溢位，此運算子會呼叫`AtlThrow`，描述錯誤的 HRESULT。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&57;](../../atl/codesnippet/cpp/ccomcurrency-class_5.cpp)]  
  
##  <a name="a-nameoperatorstareqa--ccomcurrencyoperator-"></a><a name="operator_star_eq"></a>CComCurrency::operator * =  
 此運算子用在 `CComCurrency` 物件上執行乘法並指派結果。  
  
```
const CComCurrency& operator*= (long nOperand);
const CComCurrency& operator*= (const CComCurrency& cur);
```  
  
### <a name="parameters"></a>參數  
 `nOperand`  
 乘數。  
  
 `cur`  
 `CComCurrency`物件做為乘數。  
  
### <a name="return-value"></a>傳回值  
 傳回更新`CComCurrency`物件。 如果發生錯誤，例如溢位，此運算子會呼叫`AtlThrow`，描述錯誤的 HRESULT。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&58;](../../atl/codesnippet/cpp/ccomcurrency-class_6.cpp)]  
  
##  <a name="a-nameoperatordiva--ccomcurrencyoperator-"></a><a name="operator_div"></a>CComCurrency::operator /  
 此運算子用在 `CComCurrency` 物件上執行除法。  
  
```
CComCurrency operator/(long nOperand) const;
```  
  
### <a name="parameters"></a>參數  
 `nOperand`  
 除數。  
  
### <a name="return-value"></a>傳回值  
 傳回`CComCurrency`物件，代表除法運算的結果。 如果除數為 0，就會發生判斷提示失敗。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&59;](../../atl/codesnippet/cpp/ccomcurrency-class_7.cpp)]  
  
##  <a name="a-nameoperatordiveqa--ccomcurrencyoperator-"></a><a name="operator_div_eq"></a>CComCurrency::operator / =  
 此運算子用在 `CComCurrency` 物件上執行除法並指派結果。  
  
```
const CComCurrency& operator/= (long nOperand);
```  
  
### <a name="parameters"></a>參數  
 `nOperand`  
 除數。  
  
### <a name="return-value"></a>傳回值  
 傳回更新`CComCurrency`物件。 如果除數為 0，就會發生判斷提示失敗。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&60;](../../atl/codesnippet/cpp/ccomcurrency-class_8.cpp)]  
  
##  <a name="a-nameoperatoradda--ccomcurrencyoperator-"></a><a name="operator_add"></a>CComCurrency::operator +  
 此運算子用在 `CComCurrency` 物件上執行加法。  
  
```
CComCurrency operator+(const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>參數  
 `cur`  
 `CComCurrency`来加入至原始物件的物件。  
  
### <a name="return-value"></a>傳回值  
 傳回`CComCurrency`物件，代表相加的結果。 如果發生錯誤，例如溢位，此運算子會呼叫`AtlThrow`，描述錯誤的 HRESULT。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&61;](../../atl/codesnippet/cpp/ccomcurrency-class_9.cpp)]  
  
##  <a name="a-nameoperatoraddeqa--ccomcurrencyoperator-"></a><a name="operator_add_eq"></a>CComCurrency::operator + =  
 此運算子用在 `CComCurrency` 物件上執行加法並指派結果給目前物件。  
  
```
const CComCurrency& operator+= (const CComCurrency& cur);
```  
  
### <a name="parameters"></a>參數  
 `cur`  
 `CComCurrency` 物件。  
  
### <a name="return-value"></a>傳回值  
 傳回更新`CComCurrency`物件。 如果發生錯誤，例如溢位，此運算子會呼叫`AtlThrow`，描述錯誤的 HRESULT。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&62;](../../atl/codesnippet/cpp/ccomcurrency-class_10.cpp)]  
  
##  <a name="a-nameoperatorlta--ccomcurrencyoperator-lt"></a><a name="operator_lt"></a>CComCurrency::operator&lt;  
 此運算子比較兩個 `CComCurrency` 物件來判斷何者較小。  
  
```
bool operator<(const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>參數  
 `cur`  
 `CComCurrency` 物件。  
  
### <a name="return-value"></a>傳回值  
 傳回**true**的第一個物件是否小於第二個， **false**否則。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&63;](../../atl/codesnippet/cpp/ccomcurrency-class_11.cpp)]  
  
##  <a name="a-nameoperatorlteqa--ccomcurrencyoperator-lt"></a><a name="operator_lt_eq"></a>CComCurrency::operator&lt;=  
 此運算子比較兩個 `CComCurrency` 物件來判斷是否相等或何者較小。  
  
```
bool operator<= (const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>參數  
 `cur`  
 `CComCurrency` 物件。  
  
### <a name="return-value"></a>傳回值  
 傳回**true**的第一個物件是否小於或等於第二個， **false**否則。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&64;](../../atl/codesnippet/cpp/ccomcurrency-class_12.cpp)]  
  
##  <a name="a-nameoperatoreqa--ccomcurrencyoperator-"></a><a name="operator_eq"></a>CComCurrency::operator =  
 此運算子將 `CComCurrency` 物件指派給新的值。  
  
```
const CComCurrency& operator= (const CComCurrency& curSrc) throw();
const CComCurrency& operator= (CURRENCY cySrc) throw();
const CComCurrency& operator= (FLOAT fSrc);
const CComCurrency& operator= (SHORT sSrc);
const CComCurrency& operator= (LONG lSrc);
const CComCurrency& operator= (BYTE bSrc);
const CComCurrency& operator= (USHORT usSrc);
const CComCurrency& operator= (DOUBLE dSrc);
const CComCurrency& operator= (CHAR cSrc);
const CComCurrency& operator= (ULONG ulSrc);
const CComCurrency& operator= (DECIMAL dSrc);
```  
  
### <a name="parameters"></a>參數  
 `curSrc`  
 A **CComCurrency**物件。  
  
 `cySrc`  
 型別的變數**貨幣**。  
  
 *sSrc*, `fSrc`, `lSrc`, *bSrc*, *usSrc*, `dSrc`, *cSrc*, *ulSrc*,`dSrc`  
 若要指派給數值`CComCurrency`物件。  
  
### <a name="return-value"></a>傳回值  
 傳回更新`CComCurrency`物件。 如果發生錯誤，例如溢位，此運算子會呼叫`AtlThrow`，描述錯誤的 HRESULT。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&65;](../../atl/codesnippet/cpp/ccomcurrency-class_13.cpp)]  
  
##  <a name="a-nameoperator-eqa--ccomcurrencyoperator--"></a><a name="operator_-_eq"></a>CComCurrency::operator =  
 此運算子用在 `CComCurrency` 物件上執行減法並指派結果。  
  
```
const CComCurrency& operator-= (const CComCurrency& cur);
```  
  
### <a name="parameters"></a>參數  
 `cur`  
 `CComCurrency` 物件。  
  
### <a name="return-value"></a>傳回值  
 傳回更新`CComCurrency`物件。 如果發生錯誤，例如溢位，此運算子會呼叫`AtlThrow`，描述錯誤的 HRESULT。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&66;](../../atl/codesnippet/cpp/ccomcurrency-class_14.cpp)]  
  
##  <a name="a-nameoperatoreqeqa--ccomcurrencyoperator-"></a><a name="operator_eq_eq"></a>CComCurrency::operator = =  
 此運算子比較兩個 `CComCurrency` 物件是否相等。  
  
```
bool operator== (const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>參數  
 `cur`  
 `CComCurrency`来比較的物件。  
  
### <a name="return-value"></a>傳回值  
 傳回**true**物件是否相等 (也就是`m_currency`資料成員，這兩個整數和小數，在物件具有相同的值)， **false**否則。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&67;](../../atl/codesnippet/cpp/ccomcurrency-class_15.cpp)]  
  
##  <a name="a-nameoperatorgta--ccomcurrencyoperator-gt"></a><a name="operator_gt"></a>CComCurrency::operator&gt;  
 此運算子比較兩個 `CComCurrency` 物件來判斷何者較大。  
  
```
bool operator>(const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>參數  
 `cur`  
 `CComCurrency` 物件。  
  
### <a name="return-value"></a>傳回值  
 傳回**true**的第一個物件是否大於第二個， **false**否則。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&68;](../../atl/codesnippet/cpp/ccomcurrency-class_16.cpp)]  
  
##  <a name="a-nameoperatorgteqa--ccomcurrencyoperator-gt"></a><a name="operator_gt_eq"></a>CComCurrency::operator&gt;=  
 此運算子比較兩個 `CComCurrency` 物件來判斷是否相等或何者較大。  
  
```
bool operator>= (const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>參數  
 `cur`  
 `CComCurrency` 物件。  
  
### <a name="return-value"></a>傳回值  
 傳回**true**的第一個物件是否大於或等於第二個， **false**否則。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&69;](../../atl/codesnippet/cpp/ccomcurrency-class_17.cpp)]  
  
##  <a name="a-nameoperatorcurrencya--ccomcurrencyoperator-currency"></a><a name="operator_currency"></a>CComCurrency::operator 貨幣  
 這些運算子用來轉換`CComCurrency`物件傳遞給**貨幣**資料型別。  
  
```  
operator CURRENCY&() throw();
operator const CURRENCY&() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 將參考傳回給**貨幣**物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&70;](../../atl/codesnippet/cpp/ccomcurrency-class_18.cpp)]  
  
##  <a name="a-namerounda--ccomcurrencyround"></a><a name="round"></a>CComCurrency::Round  
 呼叫這個方法要捨入至指定的小數位數的貨幣。  
  
```
HRESULT Roundint nDecimals);
```  
  
### <a name="parameters"></a>參數  
 *nDecimals*  
 數字的數目`m_currency`會捨去，範圍 0 到 4。  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功 」 或 「 錯誤`HRESULT`失敗。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&52;](../../atl/codesnippet/cpp/ccomcurrency-class_19.cpp)]  
  
##  <a name="a-namesetfractiona--ccomcurrencysetfraction"></a><a name="setfraction"></a>CComCurrency::SetFraction  
 呼叫此方法以設定 `CComCurrency` 物件的小數部分。  
  
```
HRESULT SetFraction(SHORT nFraction);
```  
  
### <a name="parameters"></a>參數  
 *nFraction*  
 要指派給的小數部分的值`m_currency`資料成員。 正負號的小數部分必須整數部分，與相同，值必須是範圍-9999 ( **CY_MIN_FRACTION**) 至 +9999 ( **CY_MAX_FRACTION**)。  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功 」 或 「 錯誤`HRESULT`失敗。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&53;](../../atl/codesnippet/cpp/ccomcurrency-class_20.cpp)]  
  
##  <a name="a-namesetintegera--ccomcurrencysetinteger"></a><a name="setinteger"></a>CComCurrency::SetInteger  
 呼叫此方法以設定 `CComCurrency` 物件的整數部分。  
  
```
HRESULT SetInteger(LONGLONG nInteger);
```  
  
### <a name="parameters"></a>參數  
 `nInteger`  
 要指派給整數部分的值`m_currency`資料成員。 正負號的整數部分必須符合現有的小數部分的符號。  
  
 `nInteger`必須在範圍內**CY_MIN_INTEGER**至**CY_MAX_INTEGER** （含)。 這些值會定義在 atlcur.h。  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功 」 或 「 錯誤`HRESULT`失敗。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&54;](../../atl/codesnippet/cpp/ccomcurrency-class_21.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [COleCurrency 類別](../../mfc/reference/colecurrency-class.md)   
 [貨幣](http://msdn.microsoft.com/en-us/5e81273c-7289-45c7-93c0-32c1553f708e)   
 [類別概觀](../../atl/atl-class-overview.md)


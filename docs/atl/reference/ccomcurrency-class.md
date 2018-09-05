---
title: CComCurrency 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComCurrency
- ATLCUR/ATL::CComCurrency
- ATLCUR/ATL::CComCurrency::CComCurrency
- ATLCUR/ATL::CComCurrency::GetCurrencyPtr
- ATLCUR/ATL::CComCurrency::GetFraction
- ATLCUR/ATL::CComCurrency::GetInteger
- ATLCUR/ATL::CComCurrency::Round
- ATLCUR/ATL::CComCurrency::SetFraction
- ATLCUR/ATL::CComCurrency::SetInteger
- ATLCUR/ATL::CComCurrency::m_currency
dev_langs:
- C++
helpviewer_keywords:
- CComCurrency class
ms.assetid: a1c3d10a-bba6-40cc-8bcf-aed9023c8a9e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1b556e724e75bb6eabc832893350126a27ad511a
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43678430"
---
# <a name="ccomcurrency-class"></a>CComCurrency 類別
`CComCurrency` 有方法和運算子可建立及管理 CURRENCY 物件。  
  
## <a name="syntax"></a>語法  
  
```
class CComCurrency
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CComCurrency::CComCurrency](#ccomcurrency)|`CComCurrency` 物件的建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CComCurrency::GetCurrencyPtr](#getcurrencyptr)|傳回 `m_currency` 資料成員的位址。|  
|[Ccomcurrency:: Getfraction](#getfraction)|呼叫此方法以傳回 `CComCurrency` 物件的小數部分。|  
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
|[CComCurrency::operator <](#operator_lt)|此運算子比較兩個 `CComCurrency` 物件來判斷何者較小。|  
|[CComCurrency::operator < =](#operator_lt_eq)|此運算子比較兩個 `CComCurrency` 物件來判斷是否相等或何者較小。|  
|[CComCurrency::operator =](#operator_eq)|此運算子將 `CComCurrency` 物件指派給新的值。|  
|[CComCurrency::operator =](#operator_-_eq)|此運算子用在 `CComCurrency` 物件上執行減法並指派結果。|  
|[CComCurrency::operator = =](#operator_eq_eq)|此運算子比較兩個 `CComCurrency` 物件是否相等。|  
|[CComCurrency::operator >](#operator_gt)|此運算子比較兩個 `CComCurrency` 物件來判斷何者較大。|  
|[CComCurrency::operator > =](#operator_gt_eq)|此運算子比較兩個 `CComCurrency` 物件來判斷是否相等或何者較大。|  
|[CComCurrency::operator 貨幣](#operator_currency)|將轉換貨幣物件。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CComCurrency::m_currency](#m_currency)|建立您的類別執行個體的貨幣變數。|  
  
## <a name="remarks"></a>備註  
 `CComCurrency` 為 CURRENCY 資料類型的包裝函式。 貨幣會實作為 10,000 調整的 8 位元組二補數整數值。 這得出一個定點數字，小數點左邊 15 位數，小數點右邊 4 位數。 CURRENCY 資料類型會非常有用，涉及金額的計算或的任何固定點計算正確性很重要。  
  
 `CComCurrency`包裝函式會實作此固定點類型的算術、 指派和比較作業。 已選取支援的應用程式來控制固定點計算期間可能發生的四捨五入錯誤。  
  
 `CComCurrency` 物件讓您分兩部分來存取小數點兩側的數字：整數部分儲存小數點左邊的值，小數部分儲存小數點右邊的值。 小數部分會在內部儲存為-9999 (CY_MIN_FRACTION) 和 + 9999 (CY_MAX_FRACTION) 之間的整數值。 此方法[ccomcurrency:: Getfraction](#getfraction)傳回值，這個值的 10000 倍 (CY_SCALE) 調整。  
  
 指定的整數和小數部分時`CComCurrency`物件，請記住小數部分是範圍 0 到 9999 之間的數字。 在處理貨幣時，例如，美元在小數點後面只以兩個有效位數來表示金額，這就很重要。 即使沒有顯示最後兩位數，也必須納入考量。  
  
|值|可能的 CComCurrency 指派|  
|-----------|---------------------------------------|  
|$10.50|CComCurrency(10,5000)*或*CComCurrency(10.50)|  
|$10.05|CComCurrency(10,500)*或*CComCurrency(10.05)|  
  
 Atlcur.h 中定義 CY_MIN_FRACTION、 CY_MAX_FRACTION 和 CY_SCALE 的值。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcur.h  
  
##  <a name="ccomcurrency"></a>  CComCurrency::CComCurrency  
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
 *curSrc*  
 現有的 `CComCurrency` 物件。  
  
 *cySrc*  
 貨幣類型的變數。  
  
 *bSrc*， *dSrc*， *fSrc*， *lSrc*， *sSrc*， *ulSrc，usSrc*  
 成員變數的初始值`m_currency`。  
  
 *cSrc*  
 字元，其中包含的成員變數的初始值`m_currency`。  
  
 *nInteger*， *nFraction*  
 整數和小數部分的初始的貨幣值。 請參閱[CComCurrency](../../atl/reference/ccomcurrency-class.md)如需詳細資訊的概觀。  
  
 *pDispSrc*  
 `IDispatch`指標。  
  
 *varSrc*  
 VARIANT 類型的變數。 目前執行緒的地區設定用來執行轉換。  
  
 *szSrc*  
 Unicode 或 ANSI 字串，包含起始值。 目前執行緒的地區設定用來執行轉換。  
  
### <a name="remarks"></a>備註  
 建構函式設定初始值[CComCurrency::m_currency](#m_currency)，並接受各種不同的資料類型，包括整數、 字串、 浮點數的數字、 貨幣變數和其他`CComCurrency`物件。 如果未不提供任何值，`m_currency`設為 0。  
  
 發生錯誤時，例如溢位時，缺少空的例外狀況規格的建構函式 (**throw （)**) 呼叫`AtlThrow`描述錯誤的 hresult。  
  
 使用浮點數或雙精度浮點值時指派的值，請注意`CComCurrency(10.50)`相當於`CComCurrency(10,5000)`而非`CComCurrency(10,50)`。  
  
##  <a name="getcurrencyptr"></a>  CComCurrency::GetCurrencyPtr  
 傳回 `m_currency` 資料成員的位址。  
  
```
CURRENCY* GetCurrencyPtr() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的位址`m_currency`資料成員  
  
##  <a name="getfraction"></a>  Ccomcurrency:: Getfraction  
 呼叫此方法以傳回的小數部分`CComCurrency`物件。  
  
```
SHORT GetFraction() const;
```  
  
### <a name="return-value"></a>傳回值  
 傳回的小數部分`m_currency`資料成員。  
  
### <a name="remarks"></a>備註  
 小數部分會是 4 位數之間的整數值-9999 (CY_MIN_FRACTION) 和 + 9999 (CY_MAX_FRACTION)。 `GetFraction` 傳回以 10000 (CY_SCALE) 調整此值。 Atlcur.h 中定義 CY_MIN_FRACTION CY_MAX_FRACTION 及 CY_SCALE 的值。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#50](../../atl/codesnippet/cpp/ccomcurrency-class_1.cpp)]  
  
##  <a name="getinteger"></a>  CComCurrency::GetInteger  
 呼叫這個方法來取得的整數部分`CComCurrency`物件。  
  
```
LONGLONG GetInteger() const;
```  
  
### <a name="return-value"></a>傳回值  
 傳回的整數部分`m_currency`資料成員。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#51](../../atl/codesnippet/cpp/ccomcurrency-class_2.cpp)]  
  
##  <a name="m_currency"></a>  CComCurrency::m_currency  
 貨幣資料成員。  
  
```
CURRENCY m_currency;
```  
  
### <a name="remarks"></a>備註  
 此成員包含貨幣存取和操作這個類別的方法。  
  
##  <a name="operator_-"></a>  CComCurrency::operator-  
 此運算子用在 `CComCurrency` 物件上執行減法。  
  
```
CComCurrency operator-() const;
CComCurrency operator-(const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>參數  
 *cur*  
 `CComCurrency` 物件。  
  
### <a name="return-value"></a>傳回值  
 傳回`CComCurrency`物件，表示減法運算的結果。 發生錯誤時，例如溢位，此運算子會呼叫`AtlThrow`描述錯誤的 hresult。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#55](../../atl/codesnippet/cpp/ccomcurrency-class_3.cpp)]  
  
##  <a name="operator_neq"></a>  CComCurrency::operator ！ =  
 此運算子比較兩個物件不相等。  
  
```
bool operator!= (const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>參數  
 *cur*  
 要比較的 `CComCurrency` 物件。  
  
### <a name="return-value"></a>傳回值  
 要比較的項目是否不相等，則傳回 TRUE`CComCurrency`物件; 否則為 FALSE。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#56](../../atl/codesnippet/cpp/ccomcurrency-class_4.cpp)]  
  
##  <a name="operator_star"></a>  CComCurrency::operator *  
 此運算子用在 `CComCurrency` 物件上執行乘法。  
  
```
CComCurrency operator*(long nOperand) const;
CComCurrency operator*(const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>參數  
 *nOperand*  
 乘數。  
  
 *cur*  
 `CComCurrency`做為乘數的物件。  
  
### <a name="return-value"></a>傳回值  
 傳回`CComCurrency`物件，表示乘法運算的結果。 發生錯誤時，例如溢位，此運算子會呼叫`AtlThrow`描述錯誤的 hresult。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#57](../../atl/codesnippet/cpp/ccomcurrency-class_5.cpp)]  
  
##  <a name="operator_star_eq"></a>  CComCurrency::operator \*=  
 此運算子用在 `CComCurrency` 物件上執行乘法並指派結果。  
  
```
const CComCurrency& operator*= (long nOperand);
const CComCurrency& operator*= (const CComCurrency& cur);
```  
  
### <a name="parameters"></a>參數  
 *nOperand*  
 乘數。  
  
 *cur*  
 `CComCurrency`做為乘數的物件。  
  
### <a name="return-value"></a>傳回值  
 傳回已更新`CComCurrency`物件。 發生錯誤時，例如溢位，此運算子會呼叫`AtlThrow`描述錯誤的 hresult。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#58](../../atl/codesnippet/cpp/ccomcurrency-class_6.cpp)]  
  
##  <a name="operator_div"></a>  CComCurrency::operator /  
 此運算子用在 `CComCurrency` 物件上執行除法。  
  
```
CComCurrency operator/(long nOperand) const;
```  
  
### <a name="parameters"></a>參數  
 *nOperand*  
 除數。  
  
### <a name="return-value"></a>傳回值  
 傳回`CComCurrency`物件，表示除法運算的結果。 如果除數為 0，則會發生判斷提示失敗。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#59](../../atl/codesnippet/cpp/ccomcurrency-class_7.cpp)]  
  
##  <a name="operator_div_eq"></a>  CComCurrency::operator / =  
 此運算子用在 `CComCurrency` 物件上執行除法並指派結果。  
  
```
const CComCurrency& operator/= (long nOperand);
```  
  
### <a name="parameters"></a>參數  
 *nOperand*  
 除數。  
  
### <a name="return-value"></a>傳回值  
 傳回已更新`CComCurrency`物件。 如果除數為 0，則會發生判斷提示失敗。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#60](../../atl/codesnippet/cpp/ccomcurrency-class_8.cpp)]  
  
##  <a name="operator_add"></a>  CComCurrency::operator +  
 此運算子用在 `CComCurrency` 物件上執行加法。  
  
```
CComCurrency operator+(const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>參數  
 *cur*  
 `CComCurrency`可以加入至原始物件的物件。  
  
### <a name="return-value"></a>傳回值  
 傳回`CComCurrency`物件，表示相加的結果。 發生錯誤時，例如溢位，此運算子會呼叫`AtlThrow`描述錯誤的 hresult。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#61](../../atl/codesnippet/cpp/ccomcurrency-class_9.cpp)]  
  
##  <a name="operator_add_eq"></a>  CComCurrency::operator + =  
 此運算子用在 `CComCurrency` 物件上執行加法並指派結果給目前物件。  
  
```
const CComCurrency& operator+= (const CComCurrency& cur);
```  
  
### <a name="parameters"></a>參數  
 *cur*  
 `CComCurrency` 物件。  
  
### <a name="return-value"></a>傳回值  
 傳回已更新`CComCurrency`物件。 發生錯誤時，例如溢位，此運算子會呼叫`AtlThrow`描述錯誤的 hresult。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#62](../../atl/codesnippet/cpp/ccomcurrency-class_10.cpp)]  
  
##  <a name="operator_lt"></a>  CComCurrency::operator &lt;  
 此運算子比較兩個 `CComCurrency` 物件來判斷何者較小。  
  
```
bool operator<(const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>參數  
 *cur*  
 `CComCurrency` 物件。  
  
### <a name="return-value"></a>傳回值  
 會傳回 TRUE，如果第一個物件小於第二個，FALSE 否則。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#63](../../atl/codesnippet/cpp/ccomcurrency-class_11.cpp)]  
  
##  <a name="operator_lt_eq"></a>  CComCurrency::operator &lt;=  
 此運算子比較兩個 `CComCurrency` 物件來判斷是否相等或何者較小。  
  
```
bool operator<= (const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>參數  
 *cur*  
 `CComCurrency` 物件。  
  
### <a name="return-value"></a>傳回值  
 如果第一個物件小於或等於第二個，FALSE 否則，傳回 TRUE。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#64](../../atl/codesnippet/cpp/ccomcurrency-class_12.cpp)]  
  
##  <a name="operator_eq"></a>  CComCurrency::operator =  
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
 *curSrc*  
 `CComCurrency` 物件。  
  
 *cySrc*  
 貨幣類型的變數。  
  
 *sSrc*， *fSrc*， *lSrc*， *bSrc*， *usSrc*， *dSrc*， *cSrc*， *ulSrc*， *dSrc*  
 若要指派給數值`CComCurrency`物件。  
  
### <a name="return-value"></a>傳回值  
 傳回已更新`CComCurrency`物件。 發生錯誤時，例如溢位，此運算子會呼叫`AtlThrow`描述錯誤的 hresult。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#65](../../atl/codesnippet/cpp/ccomcurrency-class_13.cpp)]  
  
##  <a name="operator_-_eq"></a>  CComCurrency::operator =  
 此運算子用在 `CComCurrency` 物件上執行減法並指派結果。  
  
```
const CComCurrency& operator-= (const CComCurrency& cur);
```  
  
### <a name="parameters"></a>參數  
 *cur*  
 `CComCurrency` 物件。  
  
### <a name="return-value"></a>傳回值  
 傳回已更新`CComCurrency`物件。 發生錯誤時，例如溢位，此運算子會呼叫`AtlThrow`描述錯誤的 hresult。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#66](../../atl/codesnippet/cpp/ccomcurrency-class_14.cpp)]  
  
##  <a name="operator_eq_eq"></a>  CComCurrency::operator = =  
 此運算子比較兩個 `CComCurrency` 物件是否相等。  
  
```
bool operator== (const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>參數  
 *cur*  
 `CComCurrency`来比較的物件。  
  
### <a name="return-value"></a>傳回值  
 如果物件相等則傳回 TRUE (也就是`m_currency`資料成員，這兩個整數和小數部分，在物件具有相同的值)，否則為 FALSE 否則。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#67](../../atl/codesnippet/cpp/ccomcurrency-class_15.cpp)]  
  
##  <a name="operator_gt"></a>  CComCurrency::operator &gt;  
 此運算子比較兩個 `CComCurrency` 物件來判斷何者較大。  
  
```
bool operator>(const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>參數  
 *cur*  
 `CComCurrency` 物件。  
  
### <a name="return-value"></a>傳回值  
 如果第一個物件大於第二個，FALSE 否則，傳回 TRUE。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#68](../../atl/codesnippet/cpp/ccomcurrency-class_16.cpp)]  
  
##  <a name="operator_gt_eq"></a>  CComCurrency::operator &gt;=  
 此運算子比較兩個 `CComCurrency` 物件來判斷是否相等或何者較大。  
  
```
bool operator>= (const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>參數  
 *cur*  
 `CComCurrency` 物件。  
  
### <a name="return-value"></a>傳回值  
 第一個物件是否大於或等於第二個，FALSE 否則會傳回 TRUE。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#69](../../atl/codesnippet/cpp/ccomcurrency-class_17.cpp)]  
  
##  <a name="operator_currency"></a>  CComCurrency::operator 貨幣  
 這些運算子用來轉換`CComCurrency`成貨幣資料類型的物件。  
  
```  
operator CURRENCY&() throw();
operator const CURRENCY&() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回貨幣物件的參考。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#70](../../atl/codesnippet/cpp/ccomcurrency-class_18.cpp)]  
  
##  <a name="round"></a>  CComCurrency::Round  
 呼叫這個方法来四捨五入到指定的小數位數的貨幣。  
  
```
HRESULT Roundint nDecimals);
```  
  
### <a name="parameters"></a>參數  
 *nDecimals*  
 數字的數目`m_currency`將被四捨五入，在範圍 0 到 4。  
  
### <a name="return-value"></a>傳回值  
 會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#52](../../atl/codesnippet/cpp/ccomcurrency-class_19.cpp)]  
  
##  <a name="setfraction"></a>  CComCurrency::SetFraction  
 呼叫此方法以設定 `CComCurrency` 物件的小數部分。  
  
```
HRESULT SetFraction(SHORT nFraction);
```  
  
### <a name="parameters"></a>參數  
 *nFraction*  
 要指派給的小數部分的值`m_currency`資料成員。 小數部分的符號必須與整數部分中，相同和值必須是範圍-9999 (CY_MIN_FRACTION) 到 + 9999 (CY_MAX_FRACTION) 中。  
  
### <a name="return-value"></a>傳回值  
 會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#53](../../atl/codesnippet/cpp/ccomcurrency-class_20.cpp)]  
  
##  <a name="setinteger"></a>  CComCurrency::SetInteger  
 呼叫此方法以設定 `CComCurrency` 物件的整數部分。  
  
```
HRESULT SetInteger(LONGLONG nInteger);
```  
  
### <a name="parameters"></a>參數  
 *nInteger*  
 要指派給整數部分的值`m_currency`資料成員。 正負號的整數部分必須符合現有的小數部分的符號。  
  
 *nInteger*必須在範圍內 CY_MAX_INTEGER 內含的 CY_MIN_INTEGER。 Atlcur.h 中定義這些值。  
  
### <a name="return-value"></a>傳回值  
 會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#54](../../atl/codesnippet/cpp/ccomcurrency-class_21.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [COleCurrency 類別](../../mfc/reference/colecurrency-class.md)   
 [貨幣](/windows/desktop/api/wtypes/ns-wtypes-tagcy)   
 [類別概觀](../../atl/atl-class-overview.md)

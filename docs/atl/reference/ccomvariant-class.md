---
title: "CComVariant 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComVariant
- ATLCOMCLI/ATL::CComVariant
- ATLCOMCLI/ATL::CComVariant::CComVariant
- ATLCOMCLI/ATL::CComVariant::Attach
- ATLCOMCLI/ATL::CComVariant::ChangeType
- ATLCOMCLI/ATL::CComVariant::Clear
- ATLCOMCLI/ATL::CComVariant::Copy
- ATLCOMCLI/ATL::CComVariant::CopyTo
- ATLCOMCLI/ATL::CComVariant::Detach
- ATLCOMCLI/ATL::CComVariant::GetSize
- ATLCOMCLI/ATL::CComVariant::ReadFromStream
- ATLCOMCLI/ATL::CComVariant::SetByRef
- ATLCOMCLI/ATL::CComVariant::WriteToStream
dev_langs:
- C++
helpviewer_keywords:
- VARIANT macro
- CComVariant class
- VARIANT macro, ATL
ms.assetid: 4d31149c-d005-44b5-a509-10f84afa2b61
caps.latest.revision: 26
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
ms.openlocfilehash: 4b01ca9da3d216603ea7efad228735edd1becbd3
ms.lasthandoff: 02/24/2017

---
# <a name="ccomvariant-class"></a>CComVariant 類別
這個類別會包裝`VARIANT`類型，提供成員，表示儲存的資料類型。  
  
## <a name="syntax"></a>語法  
  
```  
cpp
class CComVariant : public tagVARIANT  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CComVariant::CComVariant](#ccomvariant)|建構函式。|  
|[CComVariant:: ~ CComVariant](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CComVariant::Attach](#attach)|附加**VARIANT**到`CComVariant`物件。|  
|[CComVariant::ChangeType](#changetype)|將轉換`CComVariant`物件至新的類型。|  
|[CComVariant::Clear](#clear)|清除`CComVariant`物件。|  
|[CComVariant::Copy](#copy)|複製**VARIANT**到`CComVariant`物件。|  
|[CComVariant::CopyTo](#copyto)|複製的內容`CComVariant`物件。|  
|[CComVariant::Detach](#detach)|卸離基礎**VARIANT**從`CComVariant`物件。|  
|[CComVariant::GetSize](#getsize)|傳回內容的位元組數目的大小`CComVariant`物件。|  
|[CComVariant::ReadFromStream](#readfromstream)|載入**VARIANT**從資料流。|  
|[CComVariant::SetByRef](#setbyref)|初始化`CComVariant`物件，然後設定**vt**成員**VT_BYREF**。|  
|[CComVariant::WriteToStream](#writetostream)|儲存基礎**VARIANT**資料流。|  
  
### <a name="public-operators"></a>公用運算子  
  
|||  
|-|-|  
|[CComVariant::operator](#operator_lt)|指出是否`CComVariant`物件小於指定**VARIANT**。|  
|[CComVariant::operator >](#operator_gt)|指出是否`CComVariant`物件是否大於指定**VARIANT**。|  
|[運算子 ！ =](#operator_neq)|指出是否`CComVariant`物件不等於指定**VARIANT**。|  
|[運算子 =](#operator_eq)|將值指派至`CComVariant`物件。|  
|[運算子 = =](#operator_eq_eq)|指出是否`CComVariant`物件等於指定**VARIANT**。|  
  
## <a name="remarks"></a>備註  
 `CComVariant`包裝`VARIANT and VARIANTARG`型別，其中包含聯集和成員，表示的等位中儲存的資料類型。 **VARIANT**s 通常用於自動化。  
  
 `CComVariant`衍生自**VARIANT**輸入，所以您可能會使用的地方**VARIANT**可用。 例如，您可以使用**V_VT**巨集來擷取的型別`CComVariant`，也可以存取**vt**成員直接就像您在使用**VARIANT**。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `tagVARIANT`  
  
 `CComVariant`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlcomcli.h  
  
##  <a name="attach"></a>CComVariant::Attach  
 安全地清除目前的內容`CComVariant`物件中的內容複製`pSrc`到這個物件，然後設定的 variant 型別`pSrc`到`VT_EMPTY`。  
  
```
HRESULT Attach(VARIANT* pSrc);
```  
  
### <a name="parameters"></a>參數  
 `pSrc`  
 [in]指向[VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118)來附加至物件。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 所持有資料的擁有權`pSrc`轉移到`CComVariant`物件。  
  
##  <a name="ccomvariant"></a>CComVariant::CComVariant  
 每個建構函式會處理安全初始化`CComVariant`物件呼叫`VariantInit`Win32 函式或藉由設定物件的值和根據傳遞的參數類型。  
  
```
CComVariant() throw();
CComVariant(const CComVariant& varSrc);
CComVariant(const VARIANT& varSrc);
CComVariant(LPCOLESTR lpszSrc);
CComVariant(LPCSTR lpszSrc);
CComVariant(bool bSrc);
CComVariant(BYTE nSrc) throw();
CComVariant(int nSrc, VARTYPE vtSrc = VT_I4) throw();
CComVariant(unsigned int  nSrc, VARTYPE vtSrc = VT_UI4) throw();
CComVariant(shor  nSrc) throw();
CComVariant(unsigned short nSrc) throw();
CComVariant(long  nSrc, VARTYPE vtSrc = VT_I4) throw();
CComVariant(unsigned long  nSrc) throw();
CComVariant(LONGLONG  nSrc) throw();
CComVariant(ULONGLONG  nSrc) throw();
CComVariant(float  fltSrc) throw();
CComVariant(double  dblSrc, VARTYPE vtSrc = VT_R8) throw();
CComVariant(CY  cySrc) throw();
CComVariant(IDispatch* pSrc) throw();
CComVariant(IUnknown* pSrc) throw();
CComVariant(const SAFEARRAY* pSrc);
CComVariant(char  cSrc) throw();
CComVariant(const CComBSTR& bstrSrc);
```  
  
### <a name="parameters"></a>參數  
 *varSrc*  
 [in]`CComVariant`或`VARIANT`用來初始化`CComVariant`物件。 來源變數的內容會複製到目的地，而無需轉換。  
  
 `lpszSrc`  
 [in]字元字串用來初始化`CComVariant`物件。 您可以傳遞 (零結束寬 Unicode) 字元字串，將**LPCOLESTR**版本的建構函式或將 ANSI 字串設定為`LPCSTR`版本。 在任一情況下，此字串會轉換為 unicode`BSTR`配置使用**SysAllocString**。 型別`CComVariant`物件將會使用`VT_BSTR`。  
  
 `bSrc`  
 [in]`bool`用來初始化`CComVariant`物件。 `bool`引數轉換成**VARIANT_BOOL**然後再儲存。 型別`CComVariant`物件將會使用`VT_BOOL`。  
  
 `nSrc`  
 [in]`int`，**位元組**，**簡短**，**長**， **LONGLONG**， **ULONGLONG**，**不帶正負號短**， `unsigned long`，或`unsigned int`用來初始化`CComVariant`物件。 The type of the `CComVariant` object will be `VT_I4`, `VT_UI1`, `VT_I2`, `VT_I4`, **VT_I8**, **VT_UI8**, **VT_UI2**, **VT_UI4**, or **VT_UI4**, respectively.  
  
 `vtSrc`  
 [in]變數的型別。 當第一個參數是`int`，有效的類型為`VT_I4`和**VT_INT**。 當第一個參數是**長**，有效的類型為`VT_I4`和`VT_ERROR`。 當第一個參數是**雙**，有效的類型為`VT_R8`和`VT_DATE`。 當第一個參數是`unsigned int`，有效的類型為**VT_UI4**和**VT_UINT**。  
  
 `fltSrc`  
 [in]**Float**用來初始化`CComVariant`物件。 型別`CComVariant`物件將會使用`VT_R4`。  
  
 `dblSrc`  
 [in]**雙**用來初始化`CComVariant`物件。 型別`CComVariant`物件將會使用`VT_R8`。  
  
 `cySrc`  
 [in]**CY**用來初始化`CComVariant`物件。 型別`CComVariant`物件將會使用`VT_CY`。  
  
 `pSrc`  
 [in]`IDispatch`或**IUnknown**指標用來初始化`CComVariant`物件。 `AddRef`將介面指標上呼叫。 型別`CComVariant`物件將會使用**VT_DISPATCH**或**VT_UNKNOWN**分別。  
  
 或者， **SAFERRAY**指標用來初始化`CComVariant`物件。 一份**SAFEARRAY**會儲存在`CComVariant`物件。 型別`CComVariant`物件就是原始型別的組合**SAFEARRAY**和**VT_ARRAY**。  
  
 `cSrc`  
 [in]`char`用來初始化`CComVariant`物件。 型別`CComVariant`物件將會使用**VT_I1**。  
  
 `bstrSrc`  
 [in]BSTR 用來初始化`CComVariant`物件。 型別`CComVariant`物件將會使用`VT_BSTR`。  
  
### <a name="remarks"></a>備註  
 解構函式呼叫管理清除[CComVariant::Clear](#clear)。  
  
##  <a name="dtor"></a>CComVariant:: ~ CComVariant  
 解構函式。  
  
```
~CComVariant() throw();
```  
  
### <a name="remarks"></a>備註  
 這個方法會藉由呼叫管理清除[CComVariant::Clear](#clear)。  
  
##  <a name="changetype"></a>CComVariant::ChangeType  
 將轉換`CComVariant`物件至新的類型。  
  
```
HRESULT ChangeType(VARTYPE vtNew, const VARIANT* pSrc = NULL);
```  
  
### <a name="parameters"></a>參數  
 `vtNew`  
 [in]新類型`CComVariant`物件。  
  
 `pSrc`  
 [in]指標`VARIANT`其值會轉換成新的型別。 預設值是**NULL**，亦即`CComVariant`物件會就地轉換。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 如果您將值傳給`pSrc`，`ChangeType`將以此**VARIANT**做為轉換的來源。 否則，`CComVariant`物件將做為來源。  
  
##  <a name="clear"></a>CComVariant::Clear  
 清除`CComVariant`物件呼叫`VariantClear`Win32 函式。  
  
```
HRESULT Clear();
```  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 解構函式會自動呼叫**清除**。  
  
##  <a name="copy"></a>CComVariant::Copy  
 釋出`CComVariant`物件，然後將它指定一份指定**VARIANT**。  
  
```
HRESULT Copy(const VARIANT* pSrc);
```  
  
### <a name="parameters"></a>參數  
 `pSrc`  
 [in]指標[VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118)複製。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
##  <a name="copyto"></a>CComVariant::CopyTo  
 複製的內容`CComVariant`物件。  
  
```
HRESULT CopyTo(BSTR* pstrDest);
```  
  
### <a name="parameters"></a>參數  
 *pstrDest*  
 指向`BSTR`，將會收到一份內容`CComVariant`物件。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 **CComVariant**物件必須是型別`VT_BSTR`。  
  
##  <a name="detach"></a>CComVariant::Detach  
 卸離基礎**VARIANT**從`CComVariant`物件，並將物件的類型設為`VT_EMPTY`。  
  
```
HRESULT Detach(VARIANT* pDest);
```  
  
### <a name="parameters"></a>參數  
 `pDest`  
 [out]傳回基礎`VARIANT`物件的值。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 請注意，內容`VARIANT`所參考的`pDest`被指派的值和類型的呼叫前將自動清除**CComVariant**物件。  
  
##  <a name="getsize"></a>CComVariant::GetSize  
 簡單的固定大小`VARIANT`s，這個方法會傳回`sizeof`基礎的資料型別加上`sizeof(VARTYPE)`。  
  
```
ULONG GetSize() const;
```  
  
### <a name="return-value"></a>傳回值  
 以位元組為單位的目前內容的大小`CComVariant`物件。  
  
### <a name="remarks"></a>備註  
 如果`VARIANT`包含介面的指標，`GetSize`查詢`IPersistStream`或`IPersistStreamInit`。 如果成功，則傳回值是所傳回的值的低位 32 位元`GetSizeMax`加上`sizeof``CLSID`和`sizeof(VARTYPE)`。 如果介面指標是`NULL`，`GetSize`傳回`sizeof``CLSID`加上`sizeof(VARTYPE)`。 如果總大小大於`ULONG_MAX`，`GetSize`傳回`sizeof(VARTYPE)`表示錯誤。  
  
 在所有其他情況下，暫存`VARIANT`型別的`VT_BSTR`會從目前的強制轉型`VARIANT`。 這段`BSTR`計算字串的長度再加上字串本身的長度大小加上加上 null 字元的大小為`sizeof(VARTYPE)`。 如果`VARIANT`無法強制轉型為`VARIANT`型別的`VT_BSTR`，`GetSize`傳回`sizeof(VARTYPE)`。  
  
 這個方法所傳回的大小與所用的位元組數目相符[CComVariant::WriteToStream](#writetostream)成功的情況下。  
  
##  <a name="operator_eq"></a>CComVariant::operator =  
 指派值和對應型別`CComVariant`物件。  
  
```
CComVariant& operator=(const CComVariant& varSrc);
CComVariant& operator=(const VARIANT& varSrc);
CComVariant& operator=(const CComBSTR& bstrSrc);
CComVariant& operator=(LPCOLESTR lpszSrc);
CComVariant& operator=(LPCSTR lpszSrc);
CComVariant& operator=(bool bSrc);
CComVariant& operator=(BYTE nSrc) throw();
CComVariant& operator=int nSrc) throw();
CComVariant& operator=(unsigned int nSrc) throw();
CComVariant& operator=(short nSrc) throw();
CComVariant& operator=(unsigned short nSrc) throw();
CComVariant& operator=(long nSrc) throw();
CComVariant& operator=(unsigned long nSrc) throw();
CComVariant& operator=(LONGLONG nSrc) throw();
CComVariant& operator=(ULONGLONG nSrc) throw();
CComVariant& operator=(float fltSrc) throw();
CComVariant& operator=(double dblSrc) throw();
CComVariant& operator=(CY cySrc) throw();
CComVariant& operator=(IDispatch* pSrc) throw();
CComVariant& operator=(IUnknown* pSrc) throw();
CComVariant& operator=(const SAFEARRAY* pSrc);
CComVariant& operator=(char cSrc) throw();
```  
  
### <a name="parameters"></a>參數  
 *varSrc*  
 [in]`CComVariant`或[VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118)指派給`CComVariant`物件。 來源變數的內容會複製到目的地，而無需轉換。  
  
 `bstrSrc`  
 [in]要指派給 BSTR`CComVariant`物件。 型別`CComVariant`物件將會使用`VT_BSTR`。  
  
 `lpszSrc`  
 [in]若要指派給字元字串`CComVariant`物件。 您可以傳遞 (零結束寬 Unicode) 字元字串，將**LPCOLESTR**運算子或將 ANSI 字串設定為版本`LPCSTR`版本。 在任一情況下，此字串會轉換為 unicode`BSTR`配置使用**SysAllocString**。 型別`CComVariant`物件將會使用`VT_BSTR`。  
  
 `bSrc`  
 [in]`bool`指派給`CComVariant`物件。 `bool`引數轉換成**VARIANT_BOOL**然後再儲存。 型別`CComVariant`物件將會使用`VT_BOOL`。  
  
 `nSrc`  
 [in]The `int`, **BYTE**, **short**, **long**, **LONGLONG**, **ULONGLONG**, **unsigned short**, `unsigned long`, or `unsigned int` to be assigned to the `CComVariant` object. The type of the `CComVariant` object will be `VT_I4`, `VT_UI1`, `VT_I2`, `VT_I4`, **VT_I8**, **VT_UI8**, **VT_UI2**, **VT_UI4**, or **VT_UI4**, respectively.  
  
 `fltSrc`  
 [in]**Float**指派給`CComVariant`物件。 型別`CComVariant`物件將會使用`VT_R4`。  
  
 `dblSrc`  
 [in]**雙**指派給`CComVariant`物件。 型別`CComVariant`物件將會使用`VT_R8`。  
  
 `cySrc`  
 [in]**CY**指派給`CComVariant`物件。 型別`CComVariant`物件將會使用`VT_CY`。  
  
 `pSrc`  
 [in]`IDispatch`或**IUnknown**指標指派給`CComVariant`物件。 `AddRef`將介面指標上呼叫。 型別`CComVariant`物件將會使用**VT_DISPATCH**或**VT_UNKNOWN**分別。  
  
 或者， **SAFEARRAY**指標指派給`CComVariant`物件。 一份**SAFEARRAY**會儲存在`CComVariant`物件。 型別`CComVariant`物件就是原始型別的組合**SAFEARRAY**和**VT_ARRAY**。  
  
 `cSrc`  
 [in]若要指派給 char`CComVariant`物件。 型別`CComVariant`物件將會使用**VT_I1**。  
  
##  <a name="operator_eq_eq"></a>CComVariant::operator = =  
 指出是否`CComVariant`物件等於指定**VARIANT**。  
  
```
bool operator==(const VARIANT& varSrc) const throw();
```  
  
### <a name="remarks"></a>備註  
 傳回**true**如果值和型別*varSrc*是相等的值和類型，分別`CComVariant`物件。 否則， **false**。 運算子會使用使用者的預設地區設定來進行比較。  
  
 運算子會比較 variant 型別的值。 它會比較字串、 整數和浮點數，但不是陣列或記錄。  
  
##  <a name="operator_neq"></a>CComVariant::operator ！ =  
 指出是否`CComVariant`物件不等於指定**VARIANT**。  
  
```
bool operator!=(const VARIANT& varSrc) const throw();
```  
  
### <a name="remarks"></a>備註  
 傳回**true**如果值 」 或 「 型別*varSrc*不等於值或型別，分別`CComVariant`物件。 否則， **false**。 運算子會使用使用者的預設地區設定來進行比較。  
  
 運算子會比較 variant 型別的值。 它會比較字串、 整數和浮點數，但不是陣列或記錄。  
  
##  <a name="operator_lt"></a>CComVariant::operator&lt;  
 指出是否`CComVariant`物件小於指定**VARIANT**。  
  
```
bool operator<(const VARIANT& varSrc) const throw();
```  
  
### <a name="remarks"></a>備註  
 傳回**true**如果值`CComVariant`物件時的值小於*varSrc*。 否則， **false**。 運算子會使用使用者的預設地區設定來進行比較。  
  
##  <a name="operator_gt"></a>CComVariant::operator&gt;  
 指出是否`CComVariant`物件是否大於指定**VARIANT**。  
  
```
bool operator>(const VARIANT& varSrc) const throw();
```  
  
### <a name="remarks"></a>備註  
 傳回**true**如果值`CComVariant`物件的值大於*varSrc*。 否則， **false**。 運算子會使用使用者的預設地區設定來進行比較。  
  
##  <a name="readfromstream"></a>CComVariant::ReadFromStream  
 設定基礎**VARIANT**至**VARIANT**包含在指定的資料流。  
  
```
HRESULT ReadFromStream(IStream* pStream);
```  
  
### <a name="parameters"></a>參數  
 `pStream`  
 [in]指標[IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)包含資料的資料流上的介面。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 **ReadToStream**需要先前呼叫[WriteToStream](#writetostream)。  
  
##  <a name="setbyref"></a>CComVariant::SetByRef  
 初始化`CComVariant`物件，然後設定**vt**成員**VT_BYREF**。  
  
```
template < typename T >
void SetByRef(T* pT) throw();
```  
  
### <a name="parameters"></a>參數  
 `T`  
 型別**VARIANT**，例如`BSTR`， `int`，或`char`。  
  
 *pT*  
 用來初始化的指標`CComVariant`物件。  
  
### <a name="remarks"></a>備註  
 `SetByRef`已初始化的函式樣板`CComVariant`物件指標*pT* ，並設定**vt**成員**VT_BYREF**。 例如:   
  
 [!code-cpp[NVC_ATL_Utilities #&76;](../../atl/codesnippet/cpp/ccomvariant-class_1.cpp)]  
  
##  <a name="writetostream"></a>CComVariant::WriteToStream  
 儲存基礎**VARIANT**資料流。  
  
```
HRESULT WriteToStream(IStream* pStream);
```  
  
### <a name="parameters"></a>參數  
 `pStream`  
 [in]指標[IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)資料流上的介面。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)

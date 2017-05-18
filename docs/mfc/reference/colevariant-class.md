---
title: "COleVariant 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleVariant
- AFXDISP/COleVariant
- AFXDISP/COleVariant::COleVariant
- AFXDISP/COleVariant::Attach
- AFXDISP/COleVariant::ChangeType
- AFXDISP/COleVariant::Clear
- AFXDISP/COleVariant::Detach
- AFXDISP/COleVariant::GetByteArrayFromVariantArray
- AFXDISP/COleVariant::SetString
dev_langs:
- C++
helpviewer_keywords:
- Automation, parameter types
- COleVariant class
- VARIANT data type
ms.assetid: e1b5cd4a-b066-4b9b-b48b-6215ed52d998
caps.latest.revision: 24
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 753566adc5fc8e48ad31da52c2bb3f04c9e21727
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="colevariant-class"></a>COleVariant 類別
封裝[VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118)資料型別。  
  
## <a name="syntax"></a>語法  
  
```  
class COleVariant : public tagVARIANT  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[COleVariant::COleVariant](#colevariant)|建構 `COleVariant` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[COleVariant::Attach](#attach)|附加**VARIANT**到`COleVariant`。|  
|[COleVariant::ChangeType](#changetype)|變更這個變數的類型`COleVariant`物件。|  
|[COleVariant::Clear](#clear)|清除這個`COleVariant`物件。|  
|[COleVariant::Detach](#detach)|卸離**VARIANT**從`COleVariant`，並傳回**VARIANT**。|  
|[COleVariant::GetByteArrayFromVariantArray](#getbytearrayfromvariantarray)|擷取現有的變數陣列中的位元組陣列。|  
|[COleVariant::SetString](#setstring)|設定特定的型別，通常為 ANSI 字串。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[COleVariant::operator LPCVARIANT](#operator_lpcvariant)|將轉換`COleVariant`值`LPCVARIANT`。|  
|[COleVariant::operator LPVARIANT](#operator_lpvariant)|將轉換`COleVariant`物件插入`LPVARIANT`。|  
|[COleVariant::operator =](#operator_eq)|複製`COleVariant`值。|  
|[COleVariant::operator = =](#operator_eq_eq)|比較兩個`COleVariant`值。|  
|[COleVariant::operator &lt; &lt;，&gt;&gt;](#operator_lt_lt__gt_gt)|輸出`COleVariant`值`CArchive`或`CDumpContext`和輸入`COleVariant`物件從`CArchive`。|  
  
## <a name="remarks"></a>備註  
 此資料型別是 OLE automation 中使用。 具體來說， [DISPPARAMS](http://msdn.microsoft.com/en-us/a16e5a21-766e-4287-b039-13429aa78f8b)結構包含陣列的指標**VARIANT**結構。 A **DISPPARAMS**結構用來將參數傳遞至[Excepinfo](http://msdn.microsoft.com/en-us/964ade8e-9d8a-4d32-bd47-aa678912a54d)。  
  
> [!NOTE]
>  這個類別衍生自**VARIANT**結構。 這表示您可以傳遞`COleVariant`中的參數，呼叫**VARIANT** ，資料成員的**VARIANT**結構是可存取的資料成員的`COleVariant`。  
  
 這兩個相關的 MFC 類別[COleCurrency](../../mfc/reference/colecurrency-class.md)和[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)封裝的 variant 資料型別**貨幣**( `VT_CY`) 和**日期**( `VT_DATE`)。 `COleVariant`類別在 DAO 類別中廣泛使用，請參閱範例的這個類別，這些類別的典型用法[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)和[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。  
  
 如需詳細資訊，請參閱[VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118)，[貨幣](http://msdn.microsoft.com/en-us/5e81273c-7289-45c7-93c0-32c1553f708e)， [DISPPARAMS](http://msdn.microsoft.com/en-us/a16e5a21-766e-4287-b039-13429aa78f8b)，和[Excepinfo](http://msdn.microsoft.com/en-us/964ade8e-9d8a-4d32-bd47-aa678912a54d)中的項目[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 如需有關`COleVariant`類別和其使用 OLE automation 中的請參閱 「 傳遞參數中 OLE 自動化 」 文章中[自動化](../../mfc/automation.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `tagVARIANT`  
  
 `COleVariant`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdisp.h  
  
##  <a name="attach"></a>COleVariant::Attach  
 呼叫此函式附加給定[VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118)物件與目前`COleVariant`物件。  
  
```  
void Attach(VARIANT& varSrc);
```  
  
### <a name="parameters"></a>參數  
 *varSrc*  
 將現有**VARIANT**物件附加至目前`COleVariant`物件。  
  
### <a name="remarks"></a>備註  
 此函式會將[VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4)的*varSrc*到`VT_EMPTY`。  
  
 如需詳細資訊，請參閱[VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118)和[VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4)中的項目[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="colevariant"></a>COleVariant::COleVariant  
 建構 `COleVariant` 物件。  
  
```  
COleVariant(); 
COleVariant(const VARIANT& varSrc); 
COleVariant(const COleVariant& varSrc); 
COleVariant(LPCVARIANT pSrc); 
COleVariant(LPCTSTR lpszSrc); 
COleVariant(LPCTSTR lpszSrc, VARTYPE vtSrc); 
COleVariant(CString& strSrc); 
COleVariant(BYTE nSrc); 
COleVariant(short nSrc, VARTYPE vtSrc = VT_I2); 
COleVariant(long lSrc,VARTYPE vtSrc = VT_I4); 
COleVariant(const COleCurrency& curSrc); 
COleVariant(float fltSrc); 
COleVariant(double dblSrc); 
COleVariant(const COleDateTime& timeSrc); 
COleVariant(const CByteArray& arrSrc); 
COleVariant(const CLongBinary& lbSrc); 
COleVariant(LPCITEMIDLIST pidl);
```  
  
### <a name="parameters"></a>參數  
 *varSrc*  
 將現有`COleVariant`或**VARIANT**物件複製到新`COleVariant`物件。  
  
 `pSrc`  
 指標**VARIANT**會複製到新的物件`COleVariant`物件。  
  
 `lpszSrc`  
 Null 終止字串複製到新`COleVariant`物件。  
  
 `vtSrc`  
 `VARTYPE`新`COleVariant`物件。  
  
 `strSrc`  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md)物件複製到新`COleVariant`物件。  
  
 `nSrc`, `lSrc`  
 要複製到新的 `COleVariant` 物件中的數值。  
  
 `vtSrc`  
 `VARTYPE`新`COleVariant`物件。  
  
 `curSrc`  
 A [COleCurrency](../../mfc/reference/colecurrency-class.md)物件複製到新`COleVariant`物件。  
  
 `fltSrc`, `dblSrc`  
 要複製到新的 `COleVariant` 物件中的數值。  
  
 `timeSrc`  
 A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件複製到新`COleVariant`物件。  
  
 `arrSrc`  
 A [CByteArray](../../mfc/reference/cbytearray-class.md)物件複製到新`COleVariant`物件。  
  
 `lbSrc`  
 A [CLongBinary](../../mfc/reference/clongbinary-class.md)物件複製到新`COleVariant`物件。  
  
 `pidl`  
 指標[ITEMIDLIST](http://msdn.microsoft.com/library/windows/desktop/bb773321)結構複製到新`COleVariant`物件。  
  
### <a name="remarks"></a>備註  
 所有這些建構函式建立新的`COleVariant`物件初始化為指定的值。 遵循每個建構函式的簡短描述。  
  
- **COleVariant （)**建立空`COleVariant`物件， `VT_EMPTY`。  
  
- **COleVariant (** *varSrc* **)**複製現有**VARIANT**或`COleVariant`物件。 variant 類型會保留。  
  
- **COleVariant (** `pSrc` **)**複製現有**VARIANT**或`COleVariant`物件。 variant 類型會保留。  
  
- **COleVariant (** `lpszSrc` **)**將字串複製到新的物件， `VT_BSTR` (UNICODE)。  
  
- **COleVariant (** `lpszSrc` **，** `vtSrc` **)**將字串複製到新的物件。 參數`vtSrc`必須`VT_BSTR`(UNICODE) 或`VT_BSTRT`(ANSI)。  
  
- **COleVariant (** `strSrc` **)**將字串複製到新的物件， **VT_BSTR** (UNICODE)。  
  
- **COleVariant (** `nSrc` **)**將 8 位元整數複製到新的物件， `VT_UI1`。  
  
- **COleVariant (** `nSrc` **，** `vtSrc` **)**將 16 位元整數 （或布林值） 複製到新的物件。 參數`vtSrc`必須`VT_I2`或`VT_BOOL`。  
  
- **COleVariant (** `lSrc` **，** `vtSrc` **)**複製 32 位元整數 (或`SCODE`值) 到新物件。 參數`vtSrc`必須`VT_I4`， `VT_ERROR`，或`VT_BOOL`。  
  
- **COleVariant (** `curSrc` **)**複製**COleCurrency**到新的物件，值`VT_CY`。  
  
- **COleVariant (** `fltSrc` **)**將 32 位元浮點值複製到新的物件， `VT_R4`。  
  
- **COleVariant (** `dblSrc` **)**將 64 位元浮點值複製到新的物件， `VT_R8`。  
  
- **COleVariant (** `timeSrc` **)**複製`COleDateTime`到新的物件，值`VT_DATE`。  
  
- **COleVariant (** `arrSrc` **)**複製`CByteArray`成為新的物件，物件`VT_EMPTY`。  
  
- **COleVariant (** `lbSrc` **)**複製`CLongBinary`成為新的物件，物件`VT_EMPTY`。  
  
 如需有關`SCODE`，請參閱[COM 錯誤代碼結構](http://msdn.microsoft.com/library/windows/desktop/ms690088)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="changetype"></a>COleVariant::ChangeType  
 將在此變數值的型別轉換`COleVariant`物件。  
  
```  
void ChangeType(VARTYPE vartype, LPVARIANT pSrc = NULL);
```  
  
### <a name="parameters"></a>參數  
 `vartype`  
 [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4)這個`COleVariant`物件。  
  
 `pSrc`  
 指標[VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118)要轉換的物件。 如果這個值是**NULL**，則這個`COleVariant`轉換使用物件做為來源。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118)， [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4)，和[VariantChangeType](http://msdn.microsoft.com/en-us/48a51e32-95d7-4eeb-8106-f5043ffa2fd1)中的項目[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="clear"></a>COleVariant::Clear  
 清除**VARIANT**。  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>備註  
 這會設定**VARTYPE**到此物件`VT_EMPTY`。 `COleVariant`解構函式會呼叫此函式。  
  
 如需詳細資訊，請參閱`VARIANT`， `VARTYPE`，和`VariantClear`中的項目[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="detach"></a>COleVariant::Detach  
 卸離基礎[VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118)物件與這個`COleVariant`物件。  
  
```  
VARIANT Detach();
```  
  
### <a name="remarks"></a>備註  
 此函式會將[VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4)這個`COleVariant`物件傳遞給`VT_EMPTY`。  
  
> [!NOTE]
>  在呼叫**卸離**，呼叫端必須負責呼叫**Variant**上產生**VARIANT**結構。  
  
 如需詳細資訊，請參閱[VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118)， [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4)，和[Variant](http://msdn.microsoft.com/en-us/28741d81-8404-4f85-95d3-5c209ec13835)中的項目[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getbytearrayfromvariantarray"></a>COleVariant::GetByteArrayFromVariantArray  
 從現有的變數陣列擷取位元組陣列  
  
```  
void GetByteArrayFromVariantArray(CByteArray& bytes);
```  
  
### <a name="parameters"></a>參數  
 `bytes`  
 若要將現有的參考[CByteArray](../../mfc/reference/cbytearray-class.md)物件。  
  
##  <a name="operator_lpcvariant"></a>COleVariant::operator LPCVARIANT  
 此轉型運算子傳回`VARIANT`結構，其值會複製自這個`COleVariant`物件。  
  
```  
operator LPCVARIANT() const; 
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="operator_lpvariant"></a>COleVariant::operator LPVARIANT  
 呼叫此轉型運算子，來存取基礎`VARIANT`這個結構`COleVariant`物件。  
  
```  
operator LPVARIANT();
```   
  
### <a name="remarks"></a>備註  
  
> [!CAUTION]
>  變更中的值**VARIANT**結構存取此函式所傳回的指標會變更這個值`COleVariant`物件。  
  
##  <a name="operator_eq"></a>COleVariant::operator =  
 這些多載的指派運算子會將來源值複製到這`COleVariant`物件。  
  
```  
const COleVariant& operator=(const VARIANT& varSrc); 
const COleVariant& operator=(LPCVARIANT pSrc); 
const COleVariant& operator=(const COleVariant& varSrc); 
const COleVariant& operator=(const LPCTSTR lpszSrc);
const COleVariant& operator=(const CString& strSrc); 
const COleVariant& operator=(BYTE nSrc); 
const COleVariant& operator=(short nSrc); 
const COleVariant& operator=(long lSrc); 
const COleVariant& operator=(const COleCurrency& curSrc); 
const COleVariant& operator=(float fltSrc); 
const COleVariant& operator=(double dblSrc); 
const COleVariant& operator=(const COleDateTime& dateSrc); 
const COleVariant& operator=(const CByteArray& arrSrc); 
const COleVariant& operator=(const CLongBinary& lbSrc);
```  
  
### <a name="remarks"></a>備註  
 每個運算子的簡短描述如下︰  
  
- **運算子 = (** *varSrc***)**複製現有**VARIANT**或`COleVariant`成為此物件的物件。  
  
- **運算子 = (** `pSrc` **)**複製**VARIANT**物件來存取`pSrc`到此物件。  
  
- **運算子 = (** `lpszSrc` **)**將以 null 終止字串複製到這個物件，並設定**VARTYPE**到`VT_BSTR`。  
  
- **運算子 = (** `strSrc` **)**複製[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件到此物件，然後設定**VARTYPE**到`VT_BSTR`。  
  
- **運算子 = (** `nSrc` **)**將 8 位元或 16 位元整數值複製到這個物件。 如果`nSrc`是 8 位元值， **VARTYPE**這個設`VT_UI1`。 如果`nSrc`是 16 位元值和**VARTYPE**這是`VT_BOOL`、 保存; 否則，它會設定為`VT_I2`。  
  
- **運算子 = (** `lSrc` **)**將 32 位元整數值複製到這個物件。 如果**VARTYPE**這是`VT_ERROR`、 保存; 否則，它會設定為`VT_I4`。  
  
- **運算子 = (** `curSrc` **)**複製[COleCurrency](../../mfc/reference/colecurrency-class.md)物件到此物件，然後設定**VARTYPE**到`VT_CY`。  
  
- **運算子 = (** `fltSrc` **)**將 32 位元浮點值複製到這個物件，並設定**VARTYPE**到`VT_R4`。  
  
- **運算子 = (** `dblSrc` **)**將 64 位元浮點值複製到這個物件，並設定**VARTYPE**到`VT_R8`。  
  
- **運算子 = (** `dateSrc` **)**複製[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件到此物件，然後設定**VARTYPE**到`VT_DATE`。  
  
- **運算子 = (** `arrSrc` **)**複製[CByteArray](../../mfc/reference/cbytearray-class.md)物件到這個`COleVariant`物件。  
  
- **運算子 = (** `lbSrc` **)**複製[CLongBinary](../../mfc/reference/clongbinary-class.md)物件到這個`COleVariant`物件。  
  
 如需詳細資訊，請參閱[VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118)和[VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4)中的項目[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="operator_eq_eq"></a>COleVariant::operator = =  
 這個運算子比較兩個變數的值，並傳回它們相等; 如果為非零否則為 0。  
  
```  
BOOL operator==(const VARIANT& varSrc) const; 
BOOL operator==(LPCVARIANT pSrc) const;
```  
  
##  <a name="operator_lt_lt__gt_gt"></a>COleVariant::operator &lt; &lt;，&gt;&gt;  
 輸出`COleVariant`值`CArchive`或**CdumpContext**和輸入`COleVariant`物件從`CArchive`。  
  
```  
friend CDumpContext& AFXAPI operator<<(
    CDumpContext& dc,  
    OleVariant varSrc);
 
friend CArchive& AFXAPI operator<<(
    CArchive& ar,  
    COleVariant varSrc);
 
friend CArchive& AFXAPI operator>>(
    CArchive& ar,  
    COleVariant& varSrc);
```  
  
### <a name="remarks"></a>備註  
 `COleVariant`插入 ( ** < \< **) 運算子支援診斷傾印，並儲存至封存檔。 擷取 ( ** >> **) 運算子可支援從封存載入。  
  
##  <a name="setstring"></a>COleVariant::SetString  
 設定特定類型的字串。  
  
```  
void SetString(LPCTSTR lpszSrc, VARTYPE vtSrc);
```  
  
### <a name="parameters"></a>參數  
 `lpszSrc`  
 Null 終止字串複製到新`COleVariant`物件。  
  
 *VtSrc*  
 **VARTYPE**新`COleVariant`物件。  
  
### <a name="remarks"></a>備註  
 參數`vtSrc`必須`VT_BSTR`(UNICODE) 或`VT_BSTRT`(ANSI)。 `SetString`通常用來為 ANSI，設定字串的預設值為自[COleVariant::COleVariant](#colevariant)建構函式的字串或字串指標參數，並沒有**VARTYPE**是 UNICODE。  
  
 DAO 資料錄集的非 UNICODE 組建預期為 ANSI 字串。 因此，dao 函式使用`COleVariant`物件，如果您不想要建立的 UNICODE 資料錄集，您必須使用**COleVariant::COleVariant (** `lpszSrc` **，** `vtSrc` **)**形式的建構函式`vtSrc`設`VT_BSTRT`(ANSI) 或使用`SetString`與`vtSrc`設`VT_BSTRT`進行的 ANSI 字串。 例如，`CDaoRecordset`函式[CDaoRecordset::Seek](../../mfc/reference/cdaorecordset-class.md#seek)和[CDaoRecordset::SetFieldValue](../../mfc/reference/cdaorecordset-class.md#setfieldvalue)使用`COleVariant`物件做為參數。 如果 DAO 資料錄集不是 UNICODE，這些物件必須是 ANSI。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)





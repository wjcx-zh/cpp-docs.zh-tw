---
title: "COleCurrency 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleCurrency
- AFXDISP/COleCurrency
- AFXDISP/COleCurrency::COleCurrency
- AFXDISP/COleCurrency::Format
- AFXDISP/COleCurrency::GetStatus
- AFXDISP/COleCurrency::ParseCurrency
- AFXDISP/COleCurrency::SetCurrency
- AFXDISP/COleCurrency::SetStatus
- AFXDISP/COleCurrency::m_cur
- AFXDISP/COleCurrency::m_status
dev_langs: C++
helpviewer_keywords:
- COleCurrency [MFC], COleCurrency
- COleCurrency [MFC], Format
- COleCurrency [MFC], GetStatus
- COleCurrency [MFC], ParseCurrency
- COleCurrency [MFC], SetCurrency
- COleCurrency [MFC], SetStatus
- COleCurrency [MFC], m_cur
- COleCurrency [MFC], m_status
ms.assetid: 3a36e345-303f-46fb-a57c-858274378a8d
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a8d20b0f61fc7773899e671bec5b252ef2af1abf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="colecurrency-class"></a>COleCurrency 類別
封裝 OLE Automation 的 `CURRENCY` 資料類型。  
  
## <a name="syntax"></a>語法  
  
```  
class COleCurrency  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[COleCurrency::COleCurrency](#colecurrency)|建構 `COleCurrency` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[COleCurrency::Format](#format)|產生的格式化的字串表示`COleCurrency`物件。|  
|[COleCurrency::GetStatus](#getstatus)|取得這個狀態 （有效性）`COleCurrency`物件。|  
|[COleCurrency::ParseCurrency](#parsecurrency)|讀取**貨幣**從字串值並將值設定`COleCurrency`。|  
|[COleCurrency::SetCurrency](#setcurrency)|設定這個值`COleCurrency`物件。|  
|[COleCurrency::SetStatus](#setstatus)|設定這個狀態 （有效性）`COleCurrency`物件。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[運算子 =](#operator_eq)|複製`COleCurrency`值。|  
|[運算子 +、-](#operator_plus_minus)|新增、 相減，並變更的正負號`COleCurrency`值。|  
|[運算子 + =、-= 左邊](#operator_plus_minus_eq)|加入和減去`COleCurrency`值從此`COleCurrency`物件。|  
|[運算子 * /](#operator_star)|標尺`COleCurrency`值的整數值。|  
|[運算子 * =、 / =](#operator_star_div_eq)|可調整這`COleCurrency`值的整數值。|  
|[運算子 <<](#operator_stream)|輸出`COleCurrency`值設定為`CArchive`或`CDumpContext`。|  
|[運算子 >>](#operator_stream)|輸入`COleCurrency`物件從`CArchive`。|  
|[運算子貨幣](#operator_currency)|將轉換`COleCurrency`值放入**貨幣**。|  
|[運算子 = =、 <、 < =，等等。](#colecurrency_relational_operators)|比較兩個`COleCurrency`值。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[COleCurrency::m_cur](#m_cur)|包含基礎**貨幣**這個`COleCurrency`物件。|  
|[COleCurrency::m_status](#m_status)|包含的狀態`COleCurrency`物件。|  
  
## <a name="remarks"></a>備註  
 **COleCurrency**沒有基底類別。  
  
 **貨幣**會實作成 8 位元組，以 10000 倍的二補數整數值。 這得出一個定點數字，小數點左邊 15 位數，小數點右邊 4 位數。 **貨幣**資料類型是非常有用，涉及金額的計算或任何固定點計算正確性很重要。 它是其中一個可能的類型`VARIANT`OLE automation 資料類型。  
  
 **COleCurrency**也會實作此固定點類型的一些基本的算術運算。 已選取支援的作業來控制固定點計算期間發生的捨入錯誤。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `COleCurrency`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdisp.h  
  
##  <a name="colecurrency"></a>COleCurrency::COleCurrency  
 建構**COleCurrency**物件。  
  
```  
COleCurrency();  
COleCurrency(CURRENCY cySrc);  
  COleCurrency(const COleCurrency& curSrc);  
COleCurrency(const VARIANT& varSrc);

 
COleCurrency(
    long nUnits,  
    long nFractionalUnits);
```  
  
### <a name="parameters"></a>參數  
 `cySrc`  
 A**貨幣**值複製到新**COleCurrency**物件。  
  
 `curSrc`  
 現有**COleCurrency**物件複製到新**COleCurrency**物件。  
  
 *varSrc*  
 現有**VARIANT**資料結構 (可能是`COleVariant`物件) 轉換成貨幣值 ( `VT_CY`) 並複製到新**COleCurrency**物件。  
  
 `nUnits`, `nFractionalUnits`  
 表示要複製到新的單位和 (1/10 中 000's年） 之值的小數部分**COleCurrency**物件。  
  
### <a name="remarks"></a>備註  
 所有這些建構函式建立新**COleCurrency**物件初始化為指定的值。 遵循每個這些建構函式的簡短描述。 除非另有說明新的狀態**COleCurrency**項目設定為有效。  
  
- COleCurrency() 建構**COleCurrency**物件初始化為 0 （零）。  
  
- COleCurrency (`cySrc`) 建構**COleCurrency**物件從[貨幣](http://msdn.microsoft.com/en-us/5e81273c-7289-45c7-93c0-32c1553f708e)值。  
  
- COleCurrency (`curSrc`) 建構**COleCurrency**從現有物件**COleCurrency**物件。 新的物件都有來源物件相同的狀態。  
  
- COleCurrency (`varSrc`) 建構**COleCurrency**物件。 嘗試轉換[VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118)結構或`COleVariant`貨幣的物件 ( `VT_CY`) 值。 如果這個轉換成功，已轉換的值會複製到新**COleCurrency**物件。 如果不是，值**COleCurrency**物件設定為零 (0) 和其狀態變更為無效。  
  
- `COleCurrency(`nUnits`, `nFractionalUnits') 建構**COleCurrency**從指定的數值元件的物件。 如果小數部分的絕對值大於 10000，進行適當調整就的單位。 請注意，指定單位和小數部分的帶正負號的 long 值。  
  
 如需詳細資訊，請參閱[貨幣](http://msdn.microsoft.com/en-us/5e81273c-7289-45c7-93c0-32c1553f708e)和[VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) Windows SDK 中的項目。  
  
### <a name="example"></a>範例  
 下列範例會顯示零參數和兩個參數的建構函式的效果：  
  
 [!code-cpp[NVC_MFCOleContainer#10](../../mfc/codesnippet/cpp/colecurrency-class_1.cpp)]  
  
##  <a name="format"></a>COleCurrency::Format  
 呼叫此成員函式來建立格式化的貨幣值的表示法。  
  
```  
CString Format(DWORD  dwFlags = 0, LCID  lcid = LANG_USER_DEFAULT) const; 
```  
  
### <a name="parameters"></a>參數  
 `dwFlags`  
 表示地區設定的旗標。 下列旗標是貨幣：  
  
- **LOCALE_NOUSEROVERRIDE**使用系統預設地區設定，而不是自訂的使用者設定。  
  
 `lcid`  
 指出要使用來進行轉換的地區設定識別碼。  
  
### <a name="return-value"></a>傳回值  
 A`CString`包含格式化的貨幣值。  
  
### <a name="remarks"></a>備註  
 它會格式化使用的地區語言規格 （也就是地區設定識別碼） 的值。 貨幣符號不包含在傳回的值。 如果這個狀態**COleCurrency**物件為 null，傳回的值為空字串。 如果狀態不正確，則傳回字串指定字串資源**IDS_INVALID_CURRENCY**。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCOleContainer#11](../../mfc/codesnippet/cpp/colecurrency-class_2.cpp)]  
  
##  <a name="getstatus"></a>COleCurrency::GetStatus  
 呼叫此成員函式取得的狀態 （有效性） 指定**COleCurrency**物件。  
  
```  
CurrencyStatus GetStatus() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回這個狀態**COleCurrency**值。  
  
### <a name="remarks"></a>備註  
 傳回值由定義`CurrencyStatus`列舉內定義的型別**COleCurrency**類別。  
  
```  
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };  
```  
  
 如需這些狀態值的簡短說明，請參閱下列清單：  
  
- **COleCurrency::valid**指出此**COleCurrency**物件是否有效。  
  
- **COleCurrency::invalid**指出此**COleCurrency**物件無效; 也就是說，其值可能不正確。  
  
- **COleCurrency::null**指出此**COleCurrency**物件為 null，也就是已針對此物件提供任何值。 (這是 「 null 」 中的"having 沒有值時，"而不 c + + 資料庫意義**NULL**。)  
  
 狀態**COleCurrency**物件不能用在下列情況：  
  
-   如果其值設定從**VARIANT**或`COleVariant`無法轉換為貨幣值的值。  
  
-   如果此物件發生溢位或反向溢位算術指派作業期間，例如`+=`或 **\* =** 。  
  
-   如果無效的值已指派給這個物件。  
  
-   如果此物件的狀態已明確設定為無效的使用[SetStatus](#setstatus)。  
  
 如需作業的詳細資訊，可能會將狀態設為無效，請參閱下列成員函式：  
  
- [COleCurrency](#colecurrency)  
  
- [運算子 =](#operator_eq)  
  
- [運算子 +-](#operator_plus_minus)  
  
- [運算子 + = 和-= 左邊](#operator_plus_minus_eq)  
  
- [運算子 * /](#operator_star)  
  
- [運算子 * = 和 / =](#operator_star_div_eq)  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCOleContainer#12](../../mfc/codesnippet/cpp/colecurrency-class_3.cpp)]  
  
##  <a name="m_cur"></a>COleCurrency::m_cur  
 基礎[貨幣](http://msdn.microsoft.com/en-us/5e81273c-7289-45c7-93c0-32c1553f708e)這個結構**COleCurrency**物件。  
  
### <a name="remarks"></a>備註  
  
> [!CAUTION]
>  變更中的值**貨幣**結構存取此函式傳回的指標會變更這個值**COleCurrency**物件。 不會變更這個狀態**COleCurrency**物件。  
  
 如需詳細資訊，請參閱[貨幣](http://msdn.microsoft.com/en-us/5e81273c-7289-45c7-93c0-32c1553f708e)Windows SDK 中的項目。  
  
##  <a name="m_status"></a>COleCurrency::m_status  
 此資料成員的類型是列舉型別`CurrencyStatus`，定義內**COleCurrency**類別。  
  
```  
enum CurrencyStatus{  
    valid = 0,  
    invalid = 1,  
    null = 2,  
};  
```  
  
### <a name="remarks"></a>備註  
 如需這些狀態值的簡短說明，請參閱下列清單：  
  
- **COleCurrency::valid**指出此**COleCurrency**物件是否有效。  
  
- **COleCurrency::invalid**指出此**COleCurrency**物件無效; 也就是說，其值可能不正確。  
  
- **COleCurrency::null**指出此**COleCurrency**物件為 null，也就是已針對此物件提供任何值。 (這是 「 null 」 中的"having 沒有值時，"而不 c + + 資料庫意義**NULL**。)  
  
 狀態**COleCurrency**物件不能用在下列情況：  
  
-   如果其值設定從**VARIANT**或`COleVariant`無法轉換為貨幣值的值。  
  
-   如果此物件發生溢位或反向溢位算術指派作業期間，例如`+=`或 **\* =** 。  
  
-   如果無效的值已指派給這個物件。  
  
-   如果此物件的狀態已明確設定為無效的使用[SetStatus](#setstatus)。  
  
 如需作業的詳細資訊，可能會將狀態設為無效，請參閱下列成員函式：  
  
- [COleCurrency](#colecurrency)  
  
- [運算子 =](#operator_eq)  
  
- [運算子 +、-](#operator_plus_minus)  
  
- [運算子 + =、-= 左邊](#operator_plus_minus_eq)  
  
- [運算子 * /](#operator_star)  
  
- [運算子 * =、 / =](#operator_star_div_eq)  
  
    > [!CAUTION]
    >  此資料成員是針對進階程式的情況。 您應該使用內嵌成員函式[GetStatus](#getstatus)和[SetStatus](#setstatus)。 請參閱`SetStatus`的其他注意事項，關於明確設定此資料成員。  
  
##  <a name="operator_eq"></a>COleCurrency::operator =  
 這些多載的指派運算子會將來源貨幣值複製到這個**COleCurrency**物件。  
  
```  
const COleCurrency& operator=(CURRENCY cySrc);  
const COleCurrency& operator=(const COleCurrency& curSrc);  
  const COleCurrency& operator=(const VARIANT& varSrc);
```  
  
### <a name="remarks"></a>備註  
 每個運算子的簡短描述如下：  
  
- **運算子 = (** `cySrc` **)** `CURRENCY`值複製到**COleCurrency**物件，且其狀態會設定為有效。  
  
- **運算子 = (** `curSrc` **)**的值和運算元的現有狀態**COleCurrency**物件會複製到這個**COleCurrency**物件。  
  
- **運算子 = (** *varSrc* **)**如果轉換`VARIANT`值 (或[COleVariant](../../mfc/reference/colevariant-class.md)物件) 為貨幣 ( `VT_CY`) 是成功，已轉換的值會複製到這個**COleCurrency**物件，且其狀態會設定為有效。 如果轉換不成功，值**COleCurrency**物件設定為 0，其狀態變更為無效。  
  
 如需詳細資訊，請參閱[貨幣](http://msdn.microsoft.com/en-us/5e81273c-7289-45c7-93c0-32c1553f708e)和[VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) Windows SDK 中的項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCOleContainer#15](../../mfc/codesnippet/cpp/colecurrency-class_4.cpp)]  
  
##  <a name="operator_plus_minus"></a>COleCurrency::operator +、-  
 這些運算子可讓您加入和減去兩個**COleCurrency**值和彼此，並將變更的正負號**COleCurrency**值。  
  
```  
COleCurrency operator+(const COleCurrency& cur) const;  
COleCurrency operator-(const COleCurrency& cur) const;  
COleCurrency operator-() const;  
```  
  
### <a name="remarks"></a>備註  
 如果任一運算元是 null，產生的狀態**COleCurrency**值為 null。  
  
 如果算術運算造成溢位，產生**COleCurrency**值無效。  
  
 如果是不正確，而另一個運算元不是 null，產生的狀態**COleCurrency**值無效。  
  
 如需有關有效、 無效的 null 狀態值的詳細資訊，請參閱[m_status](#m_status)成員變數。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCOleContainer#16](../../mfc/codesnippet/cpp/colecurrency-class_5.cpp)]  
  
##  <a name="operator_plus_minus_eq"></a>COleCurrency::operator + =、-= 左邊  
 可讓您加入和減去**COleCurrency**值與這個**COleCurrency**物件。  
  
```  
const COleCurrency& operator+=(const COleCurrency& cur);  
const COleCurrency& operator-=(const COleCurrency& cur);
```  
  
### <a name="remarks"></a>備註  
 如果其中一個運算元為 null，這個狀態**COleCurrency**物件設定為 null。  
  
 如果算術運算造成溢位，這個狀態**COleCurrency**物件設為以不正確。  
  
 如果任一運算元無效，而且其他不是 null，這個狀態**COleCurrency**物件設為以不正確。  
  
 如需有關有效、 無效的 null 狀態值的詳細資訊，請參閱[m_status](#m_status)成員變數。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCOleContainer#17](../../mfc/codesnippet/cpp/colecurrency-class_6.cpp)]  
  
##  <a name="operator_star"></a>COleCurrency::operator * 和 /  
 可讓您調整**COleCurrency**整數的值。  
  
```  
COleCurrency operator*(long nOperand) const;  
COleCurrency operator/(long nOperand) const;  
```  
  
### <a name="remarks"></a>備註  
 如果**COleCurrency**運算元是 null，產生的狀態**COleCurrency**值為 null。  
  
 如果算術運算造成溢位或反向溢位，產生的狀態**COleCurrency**值無效。  
  
 如果**COleCurrency**運算元無效，產生的狀態**COleCurrency**值無效。  
  
 如需有關有效、 無效的 null 狀態值的詳細資訊，請參閱[m_status](#m_status)成員變數。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCOleContainer#18](../../mfc/codesnippet/cpp/colecurrency-class_7.cpp)]  
  
##  <a name="operator_star_div_eq"></a>COleCurrency::operator * =、 / =  
 可讓您調整這**COleCurrency**整數的值。  
  
```  
const COleCurrency& operator*=(long nOperand);  
const COleCurrency& operator/=(long nOperand);
```  
  
### <a name="remarks"></a>備註  
 如果**COleCurrency**運算元是 null，這個狀態**COleCurrency**物件設定為 null。  
  
 如果算術運算造成溢位，這個狀態**COleCurrency**物件設為以不正確。  
  
 如果**COleCurrency**運算元無效，這個狀態**COleCurrency**物件設為以不正確。  
  
 如需有關有效、 無效的 null 狀態值的詳細資訊，請參閱[m_status](#m_status)成員變數。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCOleContainer#19](../../mfc/codesnippet/cpp/colecurrency-class_8.cpp)]  
  
##  <a name="operator_stream"></a>COleCurrency::operator &lt; &lt;，&gt;&gt;  
 支援診斷傾印和儲存至封存。  
  
```  
friend CDumpContext& operator<<(
    CDumpContext& dc,  
    COleCurrency curSrc);
 
friend CArchive& operator<<(
    CArchive& ar,  
    COleCurrency curSrc);
 
friend CArchive& operator>>(
    CArchive& ar,  
    COleCurrency& curSrc);
```  
  
### <a name="remarks"></a>備註  
 擷取 (  **>>** ) 運算子支援從封存的載入。  
  
##  <a name="operator_currency"></a>COleCurrency::operator 貨幣  
 傳回`CURRENCY`結構，其值會複製從這個**COleCurrency**物件。  
  
```  
operator CURRENCY() const; 
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="parsecurrency"></a>COleCurrency::ParseCurrency  
 呼叫此成員函式可剖析字串以讀取貨幣值。  
  
```  
BOOL ParseCurrency(
    LPCTSTR lpszCurrency,  
    DWORD dwFlags = 0,  
    LCID lcid = LANG_USER_DEFAULT);
 
throw(CMemoryException*); 
throw(COleException*);
```  
  
### <a name="parameters"></a>參數  
 *lpszCurrency*  
 要剖析的 null 終止字串指標。  
  
 `dwFlags`  
 表示地區設定，可能是下列旗標的旗標：  
  
- **LOCALE_NOUSEROVERRIDE**使用系統預設地區設定，而不是自訂的使用者設定。  
  
 `lcid`  
 指出要使用來進行轉換的地區設定識別碼。  
  
### <a name="return-value"></a>傳回值  
 非零，如果成功轉換為貨幣值，否則為 0 的字串。  
  
### <a name="remarks"></a>備註  
 它會使用當地語言規格 （也就是地區設定識別碼） 的來源字串中的非數字字元意義。  
  
 如需地區設定識別碼值的討論，請參閱[支援多種語言](http://msdn.microsoft.com/en-us/47dc5add-232c-4268-b977-43e12da81ede)。  
  
 如果成功轉換為貨幣符號的字串值，這個值**COleCurrency**物件設定為該值和其狀態變更為有效。  
  
 如果無法將字串轉換為貨幣值，或發生數值溢位，這個狀態**COleCurrency**物件無效。  
  
 如果字串轉換失敗，因為記憶體配置錯誤，此函式會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)。 在任何其他錯誤的狀態，此函式會擲回[COleException](../../mfc/reference/coleexception-class.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCOleContainer#13](../../mfc/codesnippet/cpp/colecurrency-class_9.cpp)]  
  
##  <a name="colecurrency_relational_operators"></a>COleCurrency 關係運算子  
 比較兩個貨幣值，並傳回非零，如果條件為 true;否則便是 0。  
  
```  
BOOL operator==(const COleCurrency& cur) const;  
BOOL operator!=(const COleCurrency& cur) const;  
BOOL operator<(const COleCurrency& cur) const;  
BOOL operator>(const COleCurrency& cur) const;  
BOOL operator<=(const COleCurrency& cur) const;  
BOOL operator>=(const COleCurrency& cur) const;  
```  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  排序作業的傳回值 (  **<** ，  **\< =** ，  **>** ，  **>=** ) 是未定義的如果任一個運算元的狀態是 null 或無效。 等號比較運算子 ( `==`， `!=`) 請考慮運算元的狀態。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCOleContainer#20](../../mfc/codesnippet/cpp/colecurrency-class_10.cpp)]  
  
##  <a name="setcurrency"></a>COleCurrency::SetCurrency  
 呼叫此成員函式設定單位與小數部分，這個**COleCurrency**物件。  
  
```  
void SetCurrency(
    long nUnits,  
    long nFractionalUnits);
```  
  
### <a name="parameters"></a>參數  
 `nUnits`, `nFractionalUnits`  
 表示單位和 (1/10 中 000's年） 之值的小數部分複製到這個**COleCurrency**物件。  
  
### <a name="remarks"></a>備註  
 如果小數部分的絕對值大於 10000，會進行適當調整單位的第三個下列範例所示。  
  
 請注意，指定單位和小數部分的帶正負號的 long 值。 下列範例的第四個顯示的參數會有不同的符號時，會發生什麼事。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCOleContainer#14](../../mfc/codesnippet/cpp/colecurrency-class_11.cpp)]  
  
##  <a name="setstatus"></a>COleCurrency::SetStatus  
 呼叫此成員函式，以設定這個狀態 （有效性） **COleCurrency**物件。  
  
```  
void SetStatus(CurrencyStatus  status  );
```  
  
### <a name="parameters"></a>參數  
 *status*  
 這個新的狀態**COleCurrency**物件。  
  
### <a name="remarks"></a>備註  
 *狀態*參數值由定義`CurrencyStatus`列舉型別，其中定義**COleCurrency**類別。  
  
```  
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };  
```  
  
 如需這些狀態值的簡短說明，請參閱下列清單：  
  
- **COleCurrency::valid**指出此**COleCurrency**物件是否有效。  
  
- **COleCurrency::invalid**指出此**COleCurrency**物件無效; 也就是說，其值可能不正確。  
  
- **COleCurrency::null**指出此**COleCurrency**物件為 null，也就是已針對此物件提供任何值。 (這是 「 null 」 中的"having 沒有值時，"而不 c + + 資料庫意義**NULL**。)  
  
    > [!CAUTION]
    >  此函式是針對進階程式的情況。 此函式不會改變此物件中的資料。 它通常會用來設定為 null 或無效的狀態。 請注意，指派運算子 ([運算子 =](#operator_eq)) 和[SetCurrency](#setcurrency)不要將狀態設為根據的來源值的物件。  
  
## <a name="see-also"></a>請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleVariant 類別](../../mfc/reference/colevariant-class.md)

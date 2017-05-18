---
title: "CStrBufT 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStrBufT
- ATLSIMPSTR/ATL::CStrBufT
- ATLSIMPSTR/ATL::CStrBufT::CStrBufT
- ATLSIMPSTR/ATL::CStrBufT::SetLength
- ATLSIMPSTR/ATL::CStrBufT::AUTO_LENGTH
- ATLSIMPSTR/ATL::CStrBufT::SET_LENGTH
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], custom memory management
- CStrBufT class
- shared classes, CStrBufT
ms.assetid: 6b50fa8f-87e8-4ed4-a229-157ce128710f
caps.latest.revision: 17
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
ms.openlocfilehash: 2eb551d2db029de88aa9c1b456c44609b7fc0922
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cstrbuft-class"></a>CStrBufT 類別
這個類別提供的自動資源清除`GetBuffer`和`ReleaseBuffer`呼叫上的現有`CStringT`物件。  
  
## <a name="syntax"></a>語法  
  
```
template<typename TCharType>
class CStrBufT
```  
  
#### <a name="parameters"></a>參數  
 *TCharType*  
 字元類型`CStrBufT`類別。 可以是下列其中一項：  
  
- `char`（適用於 ANSI 字元字串）  
  
- `wchar_t`（如需 Unicode 字元字串）  
  
- **TCHAR** （適用於 ANSI 和 Unicode 字元字串）  
  
## <a name="members"></a>Members  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|說明|  
|----------|-----------------|  
|`PCXSTR`|常數字串的指標。|  
|`PXSTR`|字串的指標。|  
|`StringType`|其緩衝區是由這個類別樣板的特製化操作字串的型別。|  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CStrBufT::CStrBufT](#cstrbuft)|字串緩衝區物件建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CStrBufT::SetLength](#setlength)|設定關聯的字串物件的字元緩衝區長度。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CStrBufT::operator PCXSTR](#operator_pcxstr)|擷取**const**相關聯的字串物件的字元緩衝區的指標。|  
|[CStrBufT::operator PXSTR](#operator_pxstr)|擷取相關聯的字串物件的字元緩衝區的指標。|  
  
### <a name="public-constants"></a>公用常數  
  
|名稱|描述|  
|----------|-----------------|  
|[CStrBufT::AUTO_LENGTH](#auto_length)|自動判斷新的版本字串長度。|  
|[CStrBufT::SET_LENGTH](#set_length)|GetBuffer 次設定的字串物件的長度|  
  
## <a name="remarks"></a>備註  
 這個類別可做為包裝函式類別來取代呼叫[GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)和[ReleaseBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer)，或[GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength)和`ReleaseBuffer`。  
  
 主要設計為協助程式類別，`CStrBufT`提供便利的方式，開發人員使用的字元緩衝區的字串物件，而不需擔心如何或何時要呼叫`ReleaseBuffer`。 這可能是因為包裝函式物件超出範圍自然發生例外狀況或多個現有的程式碼路徑。造成其解構函式，以釋放字串資源。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlsimpstr.h  
  
##  <a name="auto_length"></a>CStrBufT::AUTO_LENGTH  
 自動判斷新的版本字串長度。  
  
```
static const DWORD AUTO_LENGTH = 0x01;
```  
  
### <a name="remarks"></a>備註  
 自動判斷新的版本字串長度。 此字串必須以 null 結束。  
  
##  <a name="cstrbuft"></a>CStrBufT::CStrBufT  
 建構緩衝區物件。  
  
```
CStrBufT(StringType& str, int nMinLength, DWORD dwFlags = AUTO_LENGTH) throw(...);
explicit CStrBufT(StringType& str) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `str`  
 緩衝區相關聯的字串物件。 開發人員通常會使用預先定義的 typedef **CStrBuf** ( **TCHAR**變體)， **CStrBufA** (`char`變體) 和**CStrBufW** ( `wchar_t` variant)。  
  
 *nMinLength*  
 字元緩衝區的最小長度。  
  
 `dwFlags`  
 判斷字串長度會自動決定。 可以是下列其中一項：  
  
- **AUTO_LENGTH**字串長度，則會自動判斷何時[CSimpleStringT::Release](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer)呼叫。 此字串必須以 null 結束。 預設值。  
  
- **SET_LENGTH**字串長度會設定當[CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)呼叫。  
  
### <a name="remarks"></a>備註  
 建立關聯的字串物件的字串緩衝區。 在建構期間， [CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)或[CSimpleStringT::GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength)呼叫。  
  
 請注意，複製建構函式是`private`。  
  
##  <a name="operator_pcxstr"></a>CStrBufT::operator PCXSTR  
 直接存取儲存在做為 C 樣式字串相關聯的字串物件中的字元。  
  
```  
operator PCXSTR() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 字串資料的字元指標。  
  
### <a name="remarks"></a>備註  
 呼叫此函式傳回的字串物件的字元緩衝區的指標。 String 物件的內容無法變更與這個指標。  
  
##  <a name="operator_pxstr"></a>CStrBufT::operator PXSTR  
 直接存取儲存在做為 C 樣式字串相關聯的字串物件中的字元。  
  
```
operator PXSTR() throw();
```  
  
### <a name="return-value"></a>傳回值  
 字串資料的字元指標。  
  
### <a name="remarks"></a>備註  
 呼叫此函式傳回的字串物件的字元緩衝區的指標。 開發人員可能會變更與這個指標的字串物件的內容。  
  
##  <a name="pcxstr"></a>CStrBufT::PCXSTR  
 常數字串的指標。  
  
```
typedef CSimpleStringT<TCharType>::PCXSTR PCXSTR;
```  
  
##  <a name="pxstr"></a>CStrBufT::PXSTR  
 字串的指標。  
  
```
typedef CSimpleStringT<TCharType>::PXSTR PXSTR;
```  
  
##  <a name="set_length"></a>CStrBufT::SET_LENGTH  
 設定字串物件的長度`GetBuffer`時間。  
  
```
static const DWORD SET_LENGTH = 0x02;
```  
  
### <a name="remarks"></a>備註  
 在 GetBuffer 階段設定的字串物件的長度。  
  
 決定如果[CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)和[CSimpleStringT::GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength)建構字串緩衝區物件時，會呼叫。  
  
##  <a name="setlength"></a>CStrBufT::SetLength  
 設定字元緩衝區的長度。  
  
```
void SetLength(int nLength);
```  
  
### <a name="parameters"></a>參數  
 `nLength`  
 字元緩衝區的字串物件的新長度。  
  
> [!NOTE]
>  必須是小於或等於指定的建構函式中的最小緩衝區長度`CStrBufT`。  
  
### <a name="remarks"></a>備註  
 呼叫此函式可設定的緩衝區物件所代表的字串長度。  
  
##  <a name="stringtype"></a>CStrBufT::StringType  
 其緩衝區是由這個類別樣板的特製化操作字串的型別。  
  
```
typedef CSimpleStringT<TCharType> StringType;
```  
  
### <a name="remarks"></a>備註  
 **TCharType**是用來特製化類別樣板的字元類型。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)




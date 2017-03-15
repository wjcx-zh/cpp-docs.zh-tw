---
title: "CW2WEX 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CW2WEX
- ATL.CW2WEX<t_nBufferLength>
- ATL::CW2WEX
- ATL.CW2WEX
- ATL::CW2WEX<t_nBufferLength>
dev_langs:
- C++
helpviewer_keywords:
- CW2WEX class
ms.assetid: 46262e56-e0d2-41fe-855b-0b67ecc8fcd7
caps.latest.revision: 20
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 9382f8404c1469b3f847500f35ab26499b6579bc
ms.lasthandoff: 02/24/2017

---
# <a name="cw2wex-class"></a>CW2WEX 類別
這個類別由字串轉換巨集`CW2TEX`和`CT2WEX`，和 typedef `CW2W`。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template <int t_nBufferLength = 128>  
class CW2WEX
```  
  
#### <a name="parameters"></a>參數  
 `t_nBufferLength`  
 轉譯程序中使用之緩衝區的大小。 預設長度為 128 位元組。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CW2WEX::CW2WEX](#cw2wex)|建構函式。|  
|[CW2WEX:: ~ CW2WEX](#dtor)|解構函式。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CW2WEX::operator LPWSTR](#operator_lpwstr)|轉換運算子。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CW2WEX::m_psz](#m_psz)|儲存在來源字串的資料成員。|  
|[CW2WEX::m_szBuffer](#m_szbuffer)|靜態緩衝區，用來儲存轉換的字串。|  
  
## <a name="remarks"></a>備註  
 除非需要額外的功能，則使用`CW2TEX`， `CT2WEX`，或`CW2W`程式碼中。  
  
 這個類別包含固定大小的靜態緩衝區可用來儲存轉換的結果。 如果結果太大，不符合靜態緩衝區，則類別會使用 `malloc` 來配置記憶體，當物件超出範圍時，即釋放記憶體。 這可確保，不同於文字轉換巨集可在舊版的 ATL，這個類別是在迴圈中使用安全的它將不會在堆疊溢位。  
  
 如果此類別會配置在堆積和失敗的記憶體，它會呼叫`AtlThrow`使用引數**E_OUTOFMEMORY**。  
  
 根據預設，ATL 轉換類別和巨集會使用目前的執行緒 ANSI 字碼頁轉換。  
  
 下列巨集根據此類別︰  
  
- `CW2TEX`  
  
- `CT2WEX`  
  
 Typedef，下列根據此類別︰  
  
- `CW2W`  
  
 如需這些文字轉換巨集的討論，請參閱[ATL 和 MFC 字串轉換巨集](http://msdn.microsoft.com/library/8f53659e-0464-4424-97db-6b8453c49863)。  
  
## <a name="example"></a>範例  
 請參閱[ATL 和 MFC 字串轉換巨集](http://msdn.microsoft.com/library/8f53659e-0464-4424-97db-6b8453c49863)如需使用這些字串轉換巨集的範例。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlconv.h  
  
##  <a name="a-namecw2wexa--cw2wexcw2wex"></a><a name="cw2wex"></a>CW2WEX::CW2WEX  
 建構函式。  
  
```
CW2WEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2WEX( LPCWSTR  psz) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `psz`  
 要轉換的文字字串。  
  
 `nCodePage`  
 字碼頁中。 不使用這個類別中。  
  
### <a name="remarks"></a>備註  
 建立做為轉換所需的緩衝區。  
  
##  <a name="a-namedtora--cw2wexcw2wex"></a><a name="dtor"></a>CW2WEX:: ~ CW2WEX  
 解構函式...  
  
```
~CW2WEX() throw();
```  
  
### <a name="remarks"></a>備註  
 釋出配置的緩衝區。  
  
##  <a name="a-namempsza--cw2wexmpsz"></a><a name="m_psz"></a>CW2WEX::m_psz  
 儲存在來源字串的資料成員。  
  
```
LPWSTR m_psz;
```  
  
##  <a name="a-namemszbuffera--cw2wexmszbuffer"></a><a name="m_szbuffer"></a>CW2WEX::m_szBuffer  
 靜態緩衝區，用來儲存轉換的字串。  
  
```
wchar_t m_szBuffer[t_nBufferLength];
```  
  
##  <a name="a-nameoperatorlpwstra--cw2wexoperator-lpwstr"></a><a name="operator_lpwstr"></a>CW2WEX::operator LPWSTR  
 轉型運算子。  
  
```  
operator LPWSTR() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回文字字串做為類型`LPWSTR`。  
  
## <a name="see-also"></a>另請參閱  
 [CA2AEX 類別](../../atl/reference/ca2aex-class.md)   
 [CA2CAEX 類別](../../atl/reference/ca2caex-class.md)   
 [CA2WEX 類別](../../atl/reference/ca2wex-class.md)   
 [CW2AEX 類別](../../atl/reference/cw2aex-class.md)   
 [CW2CWEX 類別](../../atl/reference/cw2cwex-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)


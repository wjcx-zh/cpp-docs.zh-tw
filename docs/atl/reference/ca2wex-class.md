---
title: "CA2WEX 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATLCONV/CA2WEX
- ATL.CA2WEX
- ATL.CA2WEX<t_nBufferLength>
- ATL::CA2WEX
- ATL::CA2WEX<t_nBufferLength>
- CA2WEX
dev_langs:
- C++
helpviewer_keywords:
- CA2WEX class
ms.assetid: 317d9ffb-e84f-47e8-beda-57e28fb19124
caps.latest.revision: 20
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
ms.openlocfilehash: 7c1029d0d9cb1abb1980f97c9541e2c1ce40b539
ms.lasthandoff: 02/24/2017

---
# <a name="ca2wex-class"></a>CA2WEX 類別
這個類別由字串轉換巨集`CA2TEX`， `CA2CTEX`， `CT2WEX`，和`CT2CWEX`，和 typedef **CA2W**。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template <int t_nBufferLength = 128>
class CA2WEX
```  
  
#### <a name="parameters"></a>參數  
 `t_nBufferLength`  
 轉譯程序中使用之緩衝區的大小。 預設長度為 128 位元組。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CA2WEX::CA2WEX](#ca2wex)|建構函式。|  
|[CA2WEX:: ~ CA2WEX](#dtor)|解構函式。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CA2WEX::operator LPWSTR](#operator_lpwstr)|轉換運算子。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CA2WEX::m_psz](#m_psz)|儲存在來源字串的資料成員。|  
|[CA2WEX::m_szBuffer](#m_szbuffer)|靜態緩衝區，用來儲存轉換的字串。|  
  
## <a name="remarks"></a>備註  
 除非需要額外的功能，則使用`CA2TEX`， `CA2CTEX`， `CT2WEX`， `CT2CWEX`，或**CA2W**程式碼中。  
  
 這個類別包含固定大小的靜態緩衝區可用來儲存轉換的結果。 如果結果太大，不符合靜態緩衝區，則類別會使用 `malloc` 來配置記憶體，當物件超出範圍時，即釋放記憶體。 這可確保，不同於文字轉換巨集可在舊版的 ATL，這個類別是在迴圈中使用安全的它將不會在堆疊溢位。  
  
 如果此類別會配置在堆積和失敗的記憶體，它會呼叫`AtlThrow`使用引數**E_OUTOFMEMORY**。  
  
 根據預設，ATL 轉換類別和巨集會使用目前的執行緒 ANSI 字碼頁轉換。 如果您想要覆寫特定轉換的行為，請為類別的建構函式的第二個參數指定的字碼頁。  
  
 下列巨集根據此類別︰  
  
- `CA2TEX`  
  
- `CA2CTEX`  
  
- `CT2WEX`  
  
- `CT2CWEX`  
  
 Typedef，下列根據此類別︰  
  
- **CA2W**  
  
 如需這些文字轉換巨集的討論，請參閱[ATL 和 MFC 字串轉換巨集](http://msdn.microsoft.com/library/8f53659e-0464-4424-97db-6b8453c49863)。  
  
## <a name="example"></a>範例  
 請參閱[ATL 和 MFC 字串轉換巨集](http://msdn.microsoft.com/library/8f53659e-0464-4424-97db-6b8453c49863)如需使用這些字串轉換巨集的範例。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlconv.h  
  
##  <a name="a-nameca2wexa--ca2wexca2wex"></a><a name="ca2wex"></a>CA2WEX::CA2WEX  
 建構函式。  
  
```
CA2WEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2WEX(LPCSTR psz) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `psz`  
 要轉換的文字字串。  
  
 `nCodePage`  
 使用的字碼頁來執行轉換。 請參閱程式碼頁面參數討論的[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]函式[MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072)如需詳細資訊。  
  
### <a name="remarks"></a>備註  
 配置轉譯程序中使用的緩衝區。  
  
##  <a name="a-namedtora--ca2wexca2wex"></a><a name="dtor"></a>CA2WEX:: ~ CA2WEX  
 解構函式。  
  
```
~CA2WEX() throw();
```  
  
### <a name="remarks"></a>備註  
 釋出配置的緩衝區。  
  
##  <a name="a-namempsza--ca2wexmpsz"></a><a name="m_psz"></a>CA2WEX::m_psz  
 儲存在來源字串的資料成員。  
  
```
LPWSTR m_psz;
```  
  
##  <a name="a-namemszbuffera--ca2wexmszbuffer"></a><a name="m_szbuffer"></a>CA2WEX::m_szBuffer  
 靜態緩衝區，用來儲存轉換的字串。  
  
```
wchar_t m_szBuffer[t_nBufferLength];
```  
  
##  <a name="a-nameoperatorlpwstra--ca2wexoperator-lpwstr"></a><a name="operator_lpwstr"></a>CA2WEX::operator LPWSTR  
 轉換運算子。  
  
```  
operator LPWSTR() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回文字字串做為類型**LPWSTR。**  
  
## <a name="see-also"></a>另請參閱  
 [CA2AEX 類別](../../atl/reference/ca2aex-class.md)   
 [CA2CAEX 類別](../../atl/reference/ca2caex-class.md)   
 [CW2AEX 類別](../../atl/reference/cw2aex-class.md)   
 [CW2CWEX 類別](../../atl/reference/cw2cwex-class.md)   
 [CW2WEX 類別](../../atl/reference/cw2wex-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)


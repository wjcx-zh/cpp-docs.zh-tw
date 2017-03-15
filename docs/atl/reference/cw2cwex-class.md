---
title: "CW2CWEX 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CW2CWEX
- ATL::CW2CWEX
- ATL.CW2CWEX
- ATL.CW2CWEX<t_nBufferLength>
- ATL::CW2CWEX<t_nBufferLength>
dev_langs:
- C++
helpviewer_keywords:
- CW2CWEX class
ms.assetid: d654b22b-05a6-410f-a0ec-9a2cbbb4cca7
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: a85b67a58553dada36f4472ea0683e18bc775493
ms.lasthandoff: 02/24/2017

---
# <a name="cw2cwex-class"></a>CW2CWEX 類別
這個類別由字串轉換巨集`CW2CTEX`和`CT2CWEX`，和 typedef `CW2W`。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template<int t_nBufferLength = 128>  
class CW2CWEX
```  
  
#### <a name="parameters"></a>參數  
 `t_nBufferLength`  
 轉譯程序中使用之緩衝區的大小。 預設長度為 128 位元組。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CW2CWEX::CW2CWEX](#cw2cwex)|建構函式。|  
|[CW2CWEX:: ~ CW2CWEX](#dtor)|解構函式。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CW2CWEX::operator LPCWSTR](#operator_lpcwstr)|轉換運算子。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CW2CWEX::m_psz](#m_psz)|儲存在來源字串的資料成員。|  
  
## <a name="remarks"></a>備註  
 除非需要額外的功能，則使用`CW2CTEX`， `CT2CWEX`，或`CW2W`程式碼中。  
  
 這個類別會安全地在迴圈中使用，而且不會發生堆疊溢位。 根據預設，ATL 轉換類別和巨集會使用目前的執行緒 ANSI 字碼頁轉換。  
  
 下列巨集根據此類別︰  
  
- `CW2CTEX`  
  
- `CT2CWEX`  
  
 Typedef，下列根據此類別︰  
  
- `CW2W`  
  
 如需這些文字轉換巨集的討論，請參閱[ATL 和 MFC 字串轉換巨集](http://msdn.microsoft.com/library/8f53659e-0464-4424-97db-6b8453c49863)。  
  
## <a name="example"></a>範例  
 請參閱[ATL 和 MFC 字串轉換巨集](http://msdn.microsoft.com/library/8f53659e-0464-4424-97db-6b8453c49863)如需使用這些字串轉換巨集的範例。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlconv.h  
  
##  <a name="a-namecw2cwexa--cw2cwexcw2cwex"></a><a name="cw2cwex"></a>CW2CWEX::CW2CWEX  
 建構函式。  
  
```
CW2CWEX(LPCWSTR psz, UINT nCodePage) throw(...);  
CW2CWEX(LPCWSTR psz) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `psz`  
 要轉換的文字字串。  
  
 `nCodePage`  
 字碼頁中。 不使用這個類別中。  
  
### <a name="remarks"></a>備註  
 配置轉譯程序中使用的緩衝區。  
  
##  <a name="a-namedtora--cw2cwexcw2cwex"></a><a name="dtor"></a>CW2CWEX:: ~ CW2CWEX  
 解構函式。  
  
```
~CW2CWEX() throw();
```  
  
### <a name="remarks"></a>備註  
 釋出配置的緩衝區。  
  
##  <a name="a-namempsza--cw2cwexmpsz"></a><a name="m_psz"></a>CW2CWEX::m_psz  
 儲存在來源字串的資料成員。  
  
```
LPCWSTR m_psz;
```  
  
##  <a name="a-nameoperatorlpcwstra--cw2cwexoperator-lpcwstr"></a><a name="operator_lpcwstr"></a>CW2CWEX::operator LPCWSTR  
 轉換運算子。  
  
```  
operator LPCWSTR() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回文字字串做為類型**LPCWSTR。**  
  
## <a name="see-also"></a>另請參閱  
 [CA2AEX 類別](../../atl/reference/ca2aex-class.md)   
 [CA2CAEX 類別](../../atl/reference/ca2caex-class.md)   
 [CA2WEX 類別](../../atl/reference/ca2wex-class.md)   
 [CW2AEX 類別](../../atl/reference/cw2aex-class.md)   
 [CW2WEX 類別](../../atl/reference/cw2wex-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)


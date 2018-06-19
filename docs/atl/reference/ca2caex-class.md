---
title: CA2CAEX 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CA2CAEX
- ATLCONV/ATL::CA2CAEX
- ATLCONV/ATL::CA2CAEX::CA2CAEX
- ATLCONV/ATL::CA2CAEX::m_psz
dev_langs:
- C++
helpviewer_keywords:
- CA2CAEX class
ms.assetid: 388e7c1d-a144-474c-a182-b15f69a74bd8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8aa16122a1cb3a5f8378397363a45cd28ddaef6d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32357798"
---
# <a name="ca2caex-class"></a>CA2CAEX 類別
這個類別由字串轉換巨集`CA2CTEX`和`CT2CAEX`，和 typedef **CA2CA**。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template<int t_nBufferLength = 128>  
class CA2CAEX
```  
  
#### <a name="parameters"></a>參數  
 `t_nBufferLength`  
 轉譯程序中使用之緩衝區的大小。 預設長度為 128 個位元組。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CA2CAEX::CA2CAEX](#ca2caex)|建構函式。|  
|[CA2CAEX:: ~ CA2CAEX](#dtor)|解構函式。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CA2CAEX::operator LPCSTR](#operator_lpcstr)|轉換運算子。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CA2CAEX::m_psz](#m_psz)|儲存在來源字串的資料成員。|  
  
## <a name="remarks"></a>備註  
 除非需要額外的功能，則使用`CA2CTEX`， `CT2CAEX`，或**CA2CA**自己的程式碼中。  
  
 這個類別是安全地在迴圈中使用，而且不會產生堆疊溢位。 根據預設，ATL 轉換類別及巨集將使用目前的執行緒 ANSI 字碼頁，來進行轉換。  
  
 下列巨集根據此類別：  
  
- `CA2CTEX`  
  
- `CT2CAEX`  
  
 下列 typedef 根據此類別：  
  
- **CA2CA**  
  
 如需這些文字轉換巨集的討論，請參閱[ATL 和 MFC 字串轉換巨集](string-conversion-macros.md)。  
  
## <a name="example"></a>範例  
 請參閱[ATL 和 MFC 字串轉換巨集](string-conversion-macros.md)如需使用這些字串轉換巨集的範例。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlconv.h  
  
##  <a name="ca2caex"></a>  CA2CAEX::CA2CAEX  
 建構函式。  
  
```
CA2CAEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2CAEX(LPCSTR psz) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `psz`  
 要轉換的文字字串。  
  
 `nCodePage`  
 此類別中未使用。  
  
### <a name="remarks"></a>備註  
 建立做為轉換所需的緩衝區。  
  
##  <a name="dtor"></a>  CA2CAEX:: ~ CA2CAEX  
 解構函式。  
  
```
~CA2CAEX() throw();
```  
  
### <a name="remarks"></a>備註  
 釋放已配置的緩衝區。  
  
##  <a name="m_psz"></a>  CA2CAEX::m_psz  
 儲存在來源字串的資料成員。  
  
```
LPCSTR m_psz;
```  
  
##  <a name="operator_lpcstr"></a>  CA2CAEX::operator LPCSTR  
 轉換運算子。  
  
```  
operator LPCSTR() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回文字字串做為類型`LPCSTR`。  
  
## <a name="see-also"></a>另請參閱  
 [CA2AEX 類別](../../atl/reference/ca2aex-class.md)   
 [CA2WEX 類別](../../atl/reference/ca2wex-class.md)   
 [CW2AEX 類別](../../atl/reference/cw2aex-class.md)   
 [CW2CWEX 類別](../../atl/reference/cw2cwex-class.md)   
 [CW2WEX 類別](../../atl/reference/cw2wex-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

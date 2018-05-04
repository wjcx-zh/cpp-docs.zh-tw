---
title: CW2CWEX 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CW2CWEX
- ATLCONV/ATL::CW2CWEX
- ATLCONV/ATL::CW2CWEX::CW2CWEX
- ATLCONV/ATL::CW2CWEX::m_psz
dev_langs:
- C++
helpviewer_keywords:
- CW2CWEX class
ms.assetid: d654b22b-05a6-410f-a0ec-9a2cbbb4cca7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 671311b0788438d7b92dad9d9137e28cbb88df60
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
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
 轉譯程序中使用之緩衝區的大小。 預設長度為 128 個位元組。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
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
  
 這個類別是安全地在迴圈中使用，而且不會產生堆疊溢位。 根據預設，ATL 轉換類別和巨集使用目前的執行緒 ANSI 字碼頁來進行轉換。  
  
 下列巨集根據此類別：  
  
- `CW2CTEX`  
  
- `CT2CWEX`  
  
 下列 typedef 根據此類別：  
  
- `CW2W`  
  
 如需這些文字轉換巨集的討論，請參閱[ATL 和 MFC 字串轉換巨集](string-conversion-macros.md)。  
  
## <a name="example"></a>範例  
 請參閱[ATL 和 MFC 字串轉換巨集](string-conversion-macros.md)如需使用這些字串轉換巨集的範例。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlconv.h  
  
##  <a name="cw2cwex"></a>  CW2CWEX::CW2CWEX  
 建構函式。  
  
```
CW2CWEX(LPCWSTR psz, UINT nCodePage) throw(...);  
CW2CWEX(LPCWSTR psz) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `psz`  
 要轉換的文字字串。  
  
 `nCodePage`  
 字碼頁。 不使用這個類別中。  
  
### <a name="remarks"></a>備註  
 配置轉譯程序中使用的緩衝區。  
  
##  <a name="dtor"></a>  CW2CWEX:: ~ CW2CWEX  
 解構函式。  
  
```
~CW2CWEX() throw();
```  
  
### <a name="remarks"></a>備註  
 釋放已配置的緩衝區。  
  
##  <a name="m_psz"></a>  CW2CWEX::m_psz  
 儲存在來源字串的資料成員。  
  
```
LPCWSTR m_psz;
```  
  
##  <a name="operator_lpcwstr"></a>  CW2CWEX::operator LPCWSTR  
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

---
title: CA2AEX 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CA2AEX
- ATLCONV/ATL::CA2AEX
- ATLCONV/ATL::CA2AEX::CA2AEX
- ATLCONV/ATL::CA2AEX::m_psz
- ATLCONV/ATL::CA2AEX::m_szBuffer
dev_langs:
- C++
helpviewer_keywords:
- CA2AEX class
ms.assetid: 57dc65df-d9cf-4a84-99d3-6e031dde3664
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 94e9c33fb69b439cc6c99d87d00d24f60e87d780
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37882126"
---
# <a name="ca2aex-class"></a>CA2AEX 類別
這個類別會使用字串轉換巨集 CA2TEX CT2AEX 和 typedef CA2A。  
  
> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template <int t_nBufferLength = 128>
class CA2AEX
```  
  
#### <a name="parameters"></a>參數  
 *t_nBufferLength*  
 轉譯程序中使用的緩衝區大小。 預設長度為 128 位元組。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CA2AEX::CA2AEX](#ca2aex)|建構函式。|  
|[CA2AEX:: ~ CA2AEX](#dtor)|解構函式。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CA2AEX::operator LPSTR](#operator_lpstr)|轉換運算子。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CA2AEX::m_psz](#m_psz)|儲存在來源字串資料成員。|  
|[CA2AEX::m_szBuffer](#m_szbuffer)|靜態緩衝區，用來儲存已轉換的字串。|  
  
## <a name="remarks"></a>備註  
 除非需要額外的功能，使用 CA2TEX、 CT2AEX 或 CA2A 在自己的程式碼。  
  
 這個類別包含固定大小的靜態緩衝區可用來儲存轉換的結果。 如果結果太大而無法放入靜態緩衝區，類別配置的記憶體使用**malloc**，當物件超出範圍時，即釋放記憶體。 這可確保，不同於文字轉換巨集可在舊版的 ATL，這個類別能夠安全地在迴圈中使用，而且它不會堆疊溢位。  
  
 如果類別嘗試失敗與堆積上配置記憶體時，它會呼叫`AtlThrow`E_OUTOFMEMORY 引數。  
  
 根據預設，ATL 轉換類別和巨集會使用目前的執行緒 ANSI 字碼頁轉換。  
  
 下列巨集根據此類別：  
  
- CA2TEX  
  
- CT2AEX  
  
 下列的 typedef 根據此類別：  
  
- CA2A  
  
 如需這些文字轉換巨集的討論，請參閱 < [ATL 和 MFC 字串轉換巨集](string-conversion-macros.md)。  
  
## <a name="example"></a>範例  
 請參閱[ATL 和 MFC 字串轉換巨集](string-conversion-macros.md)如需使用這些字串轉換巨集的範例。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlconv.h  
  
##  <a name="ca2aex"></a>  CA2AEX::CA2AEX  
 建構函式。  
  
```
CA2AEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2AEX(LPCSTR psz) throw(...);
```  
  
### <a name="parameters"></a>參數  
 *psz*  
 要轉換的文字字串。  
  
 *nCodePage*  
 未使用這個類別中。  
  
### <a name="remarks"></a>備註  
 建立做為轉換所需的緩衝區。  
  
##  <a name="dtor"></a>  CA2AEX:: ~ CA2AEX  
 解構函式。  
  
```
~CA2AEX() throw();
```  
  
### <a name="remarks"></a>備註  
 釋放配置的緩衝區。  
  
##  <a name="m_psz"></a>  CA2AEX::m_psz  
 儲存在來源字串資料成員。  
  
```
LPSTR m_psz;
```  
  
##  <a name="m_szbuffer"></a>  CA2AEX::m_szBuffer  
 靜態緩衝區，用來儲存已轉換的字串。  
  
```
char m_szBuffer[ t_nBufferLength];
```  
  
##  <a name="operator_lpstr"></a>  CA2AEX::operator LPSTR  
 轉換運算子。  
  
```
operator LPSTR() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 當輸入 LPSTR，傳回文字字串。  
  
## <a name="see-also"></a>另請參閱  
 [CA2CAEX 類別](../../atl/reference/ca2caex-class.md)   
 [CA2WEX 類別](../../atl/reference/ca2wex-class.md)   
 [CW2AEX 類別](../../atl/reference/cw2aex-class.md)   
 [CW2CWEX 類別](../../atl/reference/cw2cwex-class.md)   
 [CW2WEX 類別](../../atl/reference/cw2wex-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
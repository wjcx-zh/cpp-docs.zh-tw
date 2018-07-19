---
title: CA2WEX 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CA2WEX
- ATLCONV/ATL::CA2WEX
- ATLCONV/ATL::CA2WEX::CA2WEX
- ATLCONV/ATL::CA2WEX::m_psz
- ATLCONV/ATL::CA2WEX::m_szBuffer
dev_langs:
- C++
helpviewer_keywords:
- CA2WEX class
ms.assetid: 317d9ffb-e84f-47e8-beda-57e28fb19124
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f19046cc825fabd2a3a41020a9f4c141dc98489e
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37882815"
---
# <a name="ca2wex-class"></a>CA2WEX 類別
這個類別會使用字串轉換巨集 CA2TEX、 CA2CTEX、 CT2WEX，和 CT2CWEX 和 typedef CA2W。  
  
> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template <int t_nBufferLength = 128>
class CA2WEX
```  
  
#### <a name="parameters"></a>參數  
 *t_nBufferLength*  
 轉譯程序中使用的緩衝區大小。 預設長度為 128 位元組。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CA2WEX::CA2WEX](#ca2wex)|建構函式。|  
|[CA2WEX:: ~ CA2WEX](#dtor)|解構函式。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CA2WEX::operator LPWSTR](#operator_lpwstr)|轉換運算子。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CA2WEX::m_psz](#m_psz)|儲存在來源字串資料成員。|  
|[CA2WEX::m_szBuffer](#m_szbuffer)|靜態緩衝區，用來儲存已轉換的字串。|  
  
## <a name="remarks"></a>備註  
 除非需要額外的功能，使用 CA2TEX、 CA2CTEX、 CT2WEX、 CT2CWEX 或 CA2W 程式碼中。  
  
 這個類別包含固定大小的靜態緩衝區可用來儲存轉換的結果。 如果結果太大而無法放入靜態緩衝區，類別配置的記憶體使用**malloc**，當物件超出範圍時，即釋放記憶體。 這可確保，不同於文字轉換巨集可在舊版的 ATL，這個類別能夠安全地在迴圈中使用，而且它不會堆疊溢位。  
  
 如果類別嘗試失敗與堆積上配置記憶體時，它會呼叫`AtlThrow`E_OUTOFMEMORY 引數。  
  
 根據預設，ATL 轉換類別和巨集會使用目前的執行緒 ANSI 字碼頁轉換。 如果您想要覆寫特定轉換，行為，請做為類別的建構函式的第二個參數指定的字碼頁。  
  
 下列巨集根據此類別：  
  
- CA2TEX  
  
- CA2CTEX  
  
- CT2WEX  
  
- CT2CWEX  
  
 下列的 typedef 根據此類別：  
  
- CA2W  
  
 如需這些文字轉換巨集的討論，請參閱 < [ATL 和 MFC 字串轉換巨集](string-conversion-macros.md)。  
  
## <a name="example"></a>範例  
 請參閱[ATL 和 MFC 字串轉換巨集](string-conversion-macros.md)如需使用這些字串轉換巨集的範例。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlconv.h  
  
##  <a name="ca2wex"></a>  CA2WEX::CA2WEX  
 建構函式。  
  
```
CA2WEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2WEX(LPCSTR psz) throw(...);
```  
  
### <a name="parameters"></a>參數  
 *psz*  
 要轉換的文字字串。  
  
 *nCodePage*  
 使用的字碼頁來執行轉換。 請參閱 Windows SDK 函式的程式碼頁面參數討論[MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072)如需詳細資訊。  
  
### <a name="remarks"></a>備註  
 配置轉譯程序中使用的緩衝區。  
  
##  <a name="dtor"></a>  CA2WEX:: ~ CA2WEX  
 解構函式。  
  
```
~CA2WEX() throw();
```  
  
### <a name="remarks"></a>備註  
 釋放配置的緩衝區。  
  
##  <a name="m_psz"></a>  CA2WEX::m_psz  
 儲存在來源字串資料成員。  
  
```
LPWSTR m_psz;
```  
  
##  <a name="m_szbuffer"></a>  CA2WEX::m_szBuffer  
 靜態緩衝區，用來儲存已轉換的字串。  
  
```
wchar_t m_szBuffer[t_nBufferLength];
```  
  
##  <a name="operator_lpwstr"></a>  CA2WEX::operator LPWSTR  
 轉換運算子。  
  
```  
operator LPWSTR() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回文字字串，當輸入 LPWSTR。  
  
## <a name="see-also"></a>另請參閱  
 [CA2AEX 類別](../../atl/reference/ca2aex-class.md)   
 [CA2CAEX 類別](../../atl/reference/ca2caex-class.md)   
 [CW2AEX 類別](../../atl/reference/cw2aex-class.md)   
 [CW2CWEX 類別](../../atl/reference/cw2cwex-class.md)   
 [CW2WEX 類別](../../atl/reference/cw2wex-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

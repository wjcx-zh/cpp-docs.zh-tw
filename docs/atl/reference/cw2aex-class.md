---
title: "CW2AEX 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CW2AEX
- ATLCONV/ATL::CW2AEX
- ATLCONV/ATL::CW2AEX::CW2AEX
- ATLCONV/ATL::CW2AEX::m_psz
- ATLCONV/ATL::CW2AEX::m_szBuffer
dev_langs:
- C++
helpviewer_keywords:
- CW2AEX class
ms.assetid: 44dc2cf5-dd30-440b-a9b9-b21b43f49843
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d135797ff6902a9a63e89a692a25919b08b47f6d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cw2aex-class"></a>CW2AEX 類別
這個類別由字串轉換巨集`CT2AEX`， `CW2TEX`， `CW2CTEX`，和`CT2CAEX`，和 typedef **CW2A**。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template<int t_nBufferLength = 128>  
class CW2AEX
```  
  
#### <a name="parameters"></a>參數  
 `t_nBufferLength`  
 轉譯程序中使用之緩衝區的大小。 預設長度為 128 個位元組。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CW2AEX::CW2AEX](#cw2aex)|建構函式。|  
|[CW2AEX:: ~ CW2AEX](#dtor)|解構函式。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CW2AEX::operator LPSTR](#operator_lpstr)|轉換運算子。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CW2AEX::m_psz](#m_psz)|儲存在來源字串的資料成員。|  
|[CW2AEX::m_szBuffer](#m_szbuffer)|靜態緩衝區，用來儲存已轉換的字串。|  
  
## <a name="remarks"></a>備註  
 除非需要額外的功能，則使用`CT2AEX`， `CW2TEX`， `CW2CTEX`， `CT2CAEX`，或**CW2A**程式碼中。  
  
 這個類別包含固定大小的靜態緩衝區可用來儲存轉換的結果。 如果結果太大，不符合靜態緩衝區，則類別會使用 `malloc` 來配置記憶體，當物件超出範圍時，即釋放記憶體。 如此可確保，不同於文字轉換巨集可用在舊版的 ATL，這個類別會安全地在迴圈中使用，而且它將不會產生堆疊溢位。  
  
 如果類別嘗試失敗與堆積上配置記憶體，它會呼叫`AtlThrow`使用引數**E_OUTOFMEMORY**。  
  
 根據預設，ATL 轉換類別和巨集使用目前的執行緒 ANSI 字碼頁來進行轉換。 如果您想要覆寫特定轉換的行為，請為類別的建構函式的第二個參數指定的字碼頁。  
  
 下列巨集根據此類別：  
  
- `CT2AEX`  
  
- `CW2TEX`  
  
- `CW2CTEX`  
  
- `CT2CAEX`  
  
 下列 typedef 根據此類別：  
  
- **CW2A**  
  
 如需這些文字轉換巨集的討論，請參閱[ATL 和 MFC 字串轉換巨集](string-conversion-macros.md)。  
  
## <a name="example"></a>範例  
 請參閱[ATL 和 MFC 字串轉換巨集](string-conversion-macros.md)如需使用這些字串轉換巨集的範例。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlconv.h  
  
##  <a name="cw2aex"></a>CW2AEX::CW2AEX  
 建構函式。  
  
```
CW2AEX(LPCWSTR psz, UINT nCodePage) throw(...);  
CW2AEX(LPCWSTR psz) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `psz`  
 要轉換的文字字串。  
  
 `nCodePage`  
 若要執行轉換所用的字碼頁。 請參閱 Windows SDK 函式的程式碼頁面參數討論[MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072)如需詳細資訊。  
  
### <a name="remarks"></a>備註  
 配置轉譯程序中使用的緩衝區。  
  
##  <a name="dtor"></a>CW2AEX:: ~ CW2AEX  
 解構函式。  
  
```
~CW2AEX() throw();
```  
  
### <a name="remarks"></a>備註  
 釋放已配置的緩衝區。  
  
##  <a name="m_psz"></a>CW2AEX::m_psz  
 儲存在來源字串的資料成員。  
  
```
LPSTR m_psz;
```  
  
##  <a name="m_szbuffer"></a>CW2AEX::m_szBuffer  
 靜態緩衝區，用來儲存已轉換的字串。  
  
```
char m_szBuffer[t_nBufferLength];
```  
  
##  <a name="operator_lpstr"></a>CW2AEX::operator LPSTR  
 轉換運算子。  
  
```  
operator LPSTR() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回文字字串做為類型**LPSTR。**  
  
## <a name="see-also"></a>請參閱  
 [CA2AEX 類別](../../atl/reference/ca2aex-class.md)   
 [CA2CAEX 類別](../../atl/reference/ca2caex-class.md)   
 [CA2WEX 類別](../../atl/reference/ca2wex-class.md)   
 [CW2CWEX 類別](../../atl/reference/cw2cwex-class.md)   
 [CW2WEX 類別](../../atl/reference/cw2wex-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

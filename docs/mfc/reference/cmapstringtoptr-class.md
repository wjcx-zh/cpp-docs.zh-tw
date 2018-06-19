---
title: CMapStringToPtr 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMapStringToPtr
- AFXCOLL/CMapStringToPtr
- AFXCOLL/CMapStringToOb::CMapStringToOb
- AFXCOLL/CMapStringToOb::GetCount
- AFXCOLL/CMapStringToOb::GetHashTableSize
- AFXCOLL/CMapStringToOb::GetNextAssoc
- AFXCOLL/CMapStringToOb::GetSize
- AFXCOLL/CMapStringToOb::GetStartPosition
- AFXCOLL/CMapStringToOb::HashKey
- AFXCOLL/CMapStringToOb::InitHashTable
- AFXCOLL/CMapStringToOb::IsEmpty
- AFXCOLL/CMapStringToOb::Lookup
- AFXCOLL/CMapStringToOb::LookupKey
- AFXCOLL/CMapStringToOb::RemoveAll
- AFXCOLL/CMapStringToOb::RemoveKey
- AFXCOLL/CMapStringToOb::SetAt
dev_langs:
- C++
helpviewer_keywords:
- CMapStringToOb [MFC], CMapStringToOb
- CMapStringToOb [MFC], GetCount
- CMapStringToOb [MFC], GetHashTableSize
- CMapStringToOb [MFC], GetNextAssoc
- CMapStringToOb [MFC], GetSize
- CMapStringToOb [MFC], GetStartPosition
- CMapStringToOb [MFC], HashKey
- CMapStringToOb [MFC], InitHashTable
- CMapStringToOb [MFC], IsEmpty
- CMapStringToOb [MFC], Lookup
- CMapStringToOb [MFC], LookupKey
- CMapStringToOb [MFC], RemoveAll
- CMapStringToOb [MFC], RemoveKey
- CMapStringToOb [MFC], SetAt
ms.assetid: 1ac11143-eb0a-4511-a662-2df0d1d9005b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1e079717d031f4e1f5de27a528384f336f45d4ce
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33367743"
---
# <a name="cmapstringtoptr-class"></a>CMapStringToPtr 類別
支援以 `CString` 物件為索引鍵的 void 指標對應。  
  
## <a name="syntax"></a>語法  
  
```  
class CMapStringToPtr : public CObject  
```  
  
## <a name="members"></a>成員  
 成員函式`CMapStringToPtr`類別成員函式類似[CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md)。 由於此相似性，您可以針對成員函式特性使用 `CMapStringToOb` 參考文件。 無論在何處看到 `CObject` 指標做為函式參數或傳回值，請用 `void` 的指標予以替代。  
  
 `BOOL CMapStringToOb::Lookup( const char* <key>,`  
  
 `CObject*& <rValue> ) const;`  
  
 例如，轉換為  
  
 `BOOL CMapStringToPtr::Lookup( LPCTSTR <key>, void*& <rValue> )`  
  
 `const;`  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMapStringToOb::CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMapStringToOb::GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|在此對應中傳回的項目數。|  
|[CMapStringToOb::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|判斷目前的雜湊表中的元素數目。|  
|[CMapStringToOb::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|取得逐一查看下一個項目。|  
|[CMapStringToOb::GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|在此對應中傳回的項目數。|  
|[CMapStringToOb::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|傳回第一個項目的位置。|  
|[CMapStringToOb::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|計算指定的索引鍵的雜湊值。|  
|[CMapStringToOb::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|初始化雜湊表。|  
|[CMapStringToOb::IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|測試的空白對應條件 （沒有項目）。|  
|[CMapStringToOb::Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|查閱根據 void 指標索引鍵的 void 指標。 指標值，而不將它所指向，實體用於比較索引鍵。|  
|[CMapStringToOb::LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|傳回與指定的索引鍵值相關聯的索引鍵的參考。|  
|[CMapStringToOb::RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|此對應中移除所有項目。|  
|[CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|移除索引鍵所指定的項目。|  
|[CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|將項目插入對應中。如果找到相符的索引鍵，會取代現有的項目。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CMapStringToOb::operator [ ]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|將項目插入對應 — 運算子替代`SetAt`。|  
  
## <a name="remarks"></a>備註  
 `CMapStringToPtr` 結合 `IMPLEMENT_DYNAMIC` 巨集，支援 `CDumpContext` 物件的執行階段類型存取和傾印。 如果您需要個別地圖元素的傾印，您必須設定為 1 或更大的傾印內容的深度。  
  
 無法序列化字串的指標對應。  
  
 當`CMapStringToPtr`物件被刪除，或當其項目會遭到移除，`CString`會移除索引鍵物件和文字。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMapStringToPtr`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxcoll.h  
  
## <a name="see-also"></a>另請參閱  
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)




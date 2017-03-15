---
title: "CMapWordToOb 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMapWordToOb
dev_langs:
- C++
helpviewer_keywords:
- 16-bit word mapping
- CMapWordToOb class
ms.assetid: 9c9bcd76-456f-4cf9-b03c-dd28b49d5e4f
caps.latest.revision: 23
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 75c3a1dd3d0a0c4fdd6c9dea37e5ed143e4cb3cc
ms.lasthandoff: 02/24/2017

---
# <a name="cmapwordtoob-class"></a>CMapWordToOb 類別
支援以 16 位元字組為索引鍵的 `CObject` 指標對應。  
  
## <a name="syntax"></a>語法  
  
```  
class CMapWordToOb : public CObject  
```  
  
## <a name="members"></a>Members  
 成員函式`CMapWordToOb`類別的成員函式類似[CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md)。 由於此相似性，您可以針對成員函式特性使用 `CMapStringToOb` 參考文件。 無論在何處看到`CString`或**const**指標`char`做為函式參數或傳回值，取代**WORD**。  
  
 `BOOL CMapStringToOb::Lookup( const char* <key>,`  
  
 `CObject*& <rValue> ) const;`  
  
 例如，轉換為  
  
 `BOOL CMapWordToOb::Lookup( WORD <key>, CObject*& <rValue> ) const;`  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMapStringToOb::CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMapStringToOb::GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|傳回這個對應中的項目數目。|  
|[CMapStringToOb::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|判斷目前的雜湊表中的元素數目。|  
|[CMapStringToOb::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|取得逐一查看下一個項目。|  
|[CMapStringToOb::GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|傳回這個對應中的項目數目。|  
|[CMapStringToOb::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|傳回第一個項目的位置。|  
|[CMapStringToOb::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|計算指定之索引鍵的雜湊值。|  
|[CMapStringToOb::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|初始化雜湊表。|  
|[CMapStringToOb::IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|測試空白對應條件 （沒有項目）。|  
|[CMapStringToOb::Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|查閱根據 void 指標索引鍵的 void 指標。 指標值，而不將它所指向，實體用於索引鍵的比較。|  
|[CMapStringToOb::LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|傳回指定之索引鍵值相關聯的索引鍵的參考。|  
|[CMapStringToOb::RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|此對應會移除所有項目。|  
|[CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|移除索引鍵所指定的項目。|  
|[CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|將項目插入對應中。如果找到相符的索引鍵，會取代現有的項目。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CMapStringToOb::operator]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|將項目插入對應 — 運算子替代`SetAt`。|  
  
## <a name="remarks"></a>備註  
 `CMapWordToOb` 引入 `IMPLEMENT_SERIAL` 巨集，以支援其項目的序列化和傾印。 如果對應儲存至封存檔，多載的插入與每個項目會依次序列化 ( ** << **) 運算子或`Serialize`成員函式。  
  
 如果您需要個別的傾印**WORD** -  `CObject`項目，您必須將傾印內容的深度大於或等於 1。  
  
 當`CMapWordToOb`物件被刪除，或當其項目被移除，`CObject`會移除指標。 所參考的物件`CObject`指標不會終結。  
  
 如需有關`CMapWordToOb`，請參閱文章[集合](../../mfc/collections.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMapWordToOb`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxcoll.h  
  
## <a name="see-also"></a>另請參閱  
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)





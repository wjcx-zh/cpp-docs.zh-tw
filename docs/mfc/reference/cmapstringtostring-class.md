---
title: "CMapStringToString 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMapStringToString
dev_langs:
- C++
helpviewer_keywords:
- collection classes, string mapping
- strings [C++], mapping
- strings [C++], class for mapping
- CMapStringToString class
ms.assetid: b45794c2-fe6b-4edb-a8ca-faa03b57b4a8
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 58ca2023d57c2865dadc8dfab304aab2fa39a96b
ms.lasthandoff: 02/24/2017

---
# <a name="cmapstringtostring-class"></a>CMapStringToString 類別
支援以 `CString` 物件為索引鍵的 `CString` 物件對應。  
  
## <a name="syntax"></a>語法  
  
```  
class CMapStringToString : public CObject  
```  
  
## <a name="members"></a>Members  
 成員函式`CMapStringToString`類別的成員函式類似[CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md)。 由於此相似性，您可以針對成員函式特性使用 `CMapStringToOb` 參考文件。 無論在何處看到`CObject`指標的傳回值或 「 輸出 」 函式參數，如指標予以替代`char`。 無論在何處看到`CObject`指標做為 「 輸入 」 函式參數的指標予以替代`char`。  
  
 `BOOL CMapStringToOb::Lookup(const char*<key>, CObject*&<rValue>) const;`  
  
 例如，轉換為  
  
 `BOOL CMapStringToString::Lookup(LPCTSTR<key>, CString&<rValue>) const;`  
  
### <a name="public-structures"></a>公用結構  
  
|名稱|描述|  
|----------|-----------------|  
|[CMapStringToString::CPair](#cpair)|巢狀的結構，其中包含的索引鍵值和相關聯的字串物件的值。|  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMapStringToOb::CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
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
|[CMapStringToString::PGetFirstAssoc](#pgetfirstassoc)|取得第一個指標`CString`對應中。|  
|[CMapStringToString::PGetNextAssoc](#pgetnextassoc)|取得下一個指標`CString`來重複。|  
|[CMapStringToString::PLookup](#plookup)|傳回的指標`CString`其值符合指定的值。|  
|[CMapStringToOb::RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|此對應會移除所有項目。|  
|[CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|移除索引鍵所指定的項目。|  
|[CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|將項目插入對應中。如果找到相符的索引鍵，會取代現有的項目。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CMapStringToOb::operator]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|將項目插入對應 — 運算子替代`SetAt`。|  
  
## <a name="remarks"></a>備註  
 `CMapStringToString` 引入 `IMPLEMENT_SERIAL` 巨集，以支援其項目的序列化和傾印。 如果對應儲存至封存檔，多載的插入與每個項目會依次序列化 ( ** << **) 運算子或`Serialize`成員函式。  
  
 如果您需要個別的傾印`CString` -  `CString`項目，您必須將傾印內容的深度大於或等於 1。  
  
 當`CMapStringToString`物件被刪除，或當其項目被移除，`CString`適當地移除物件。  
  
 如需有關`CMapStringToString`，請參閱文章[集合](../../mfc/collections.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMapStringToString`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxcoll.h  
  
##  <a name="a-namecpaira--cmapstringtostringcpair"></a><a name="cpair"></a>CMapStringToString::CPair  
 包含索引鍵的值和相關聯的字串物件的值。  
  
### <a name="remarks"></a>備註  
 這是在類別內的巢狀的結構[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)。  
  
 結構是由兩個欄位所組成︰  
  
- **索引鍵**索引鍵類型的實際值。  
  
- **值**相關聯的物件的值。  
  
 它用來儲存傳回的值[CMapStringToString::PLookup](#plookup)， [CMapStringToString::PGetFirstAssoc](#pgetfirstassoc)，和[CMapStringToString::PGetNextAssoc](#pgetnextassoc)。  
  
### <a name="example"></a>範例  
  如需使用方式的範例，請參閱範例[CMapStringToString::PLookup](#plookup)。  
  
##  <a name="a-namepgetfirstassoca--cmapstringtostringpgetfirstassoc"></a><a name="pgetfirstassoc"></a>CMapStringToString::PGetFirstAssoc  
 傳回對應物件的第一個項目。  
  
```  
const CPair* PGetFirstAssoc() const;

CPair* PGetFirstAssoc();
```  
  
### <a name="return-value"></a>傳回值  
 指向對應; 中的第一個項目請參閱[CMapStringToString::CPair](#cpair)。 如果對應是空的這個值是`NULL`。  
  
### <a name="remarks"></a>備註  
 呼叫此函式指標的第一個項目傳回 map 物件中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&73;](../../mfc/codesnippet/cpp/cmapstringtostring-class_1.cpp)]  
  
##  <a name="a-namepgetnextassoca--cmapstringtostringpgetnextassoc"></a><a name="pgetnextassoc"></a>CMapStringToString::PGetNextAssoc  
 擷取所指的對應項目`pAssocRec`。  
  
```  
const CPair *PGetNextAssoc(const CPair* pAssoc) const;  
  
CPair *PGetNextAssoc(const CPair* pAssoc);
```  
  
### <a name="parameters"></a>參數  
 *pAssoc*  
 前一個對應項目會指向[PGetNextAssoc](#pgetnextassoc)或[PGetFirstAssoc](#pgetfirstassoc)呼叫。  
  
### <a name="return-value"></a>傳回值  
 指向對應; 中的下一個項目請參閱[CMapStringToString::CPair](#cpair)。 如果項目是在對應中的最後一個，這個值是**NULL**。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來逐一查看對應中的所有項目。 擷取第一個項目，藉由呼叫`PGetFirstAssoc`，然後逐一連續呼叫來對應`PGetNextAssoc`。  
  
### <a name="example"></a>範例  
  請參閱範例[CMapStringToString::PGetFirstAssoc](#pgetfirstassoc)。  
  
##  <a name="a-nameplookupa--cmapstringtostringplookup"></a><a name="plookup"></a>CMapStringToString::PLookup  
 查閱對應至指定的索引鍵的值。  
  
```  
const CPair* PLookup(LPCTSTR key) const;

CPair* PLookup(LPCTSTR key);
```  
  
### <a name="parameters"></a>參數  
 `key`  
 要搜尋的項目索引鍵的指標。  
  
### <a name="return-value"></a>傳回值  
 指定的索引鍵的指標。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來搜尋完全符合指定的索引鍵的索引鍵的對應項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&74;](../../mfc/codesnippet/cpp/cmapstringtostring-class_2.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例收集](../../visual-cpp-samples.md)   
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)





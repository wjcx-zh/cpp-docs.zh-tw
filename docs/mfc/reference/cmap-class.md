---
title: "CMap 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMap
- AFXTEMPL/CMap
- AFXTEMPL/CMap::CPair
- AFXTEMPL/CMap::CMap
- AFXTEMPL/CMap::GetCount
- AFXTEMPL/CMap::GetHashTableSize
- AFXTEMPL/CMap::GetNextAssoc
- AFXTEMPL/CMap::GetSize
- AFXTEMPL/CMap::GetStartPosition
- AFXTEMPL/CMap::InitHashTable
- AFXTEMPL/CMap::IsEmpty
- AFXTEMPL/CMap::Lookup
- AFXTEMPL/CMap::PGetFirstAssoc
- AFXTEMPL/CMap::PGetNextAssoc
- AFXTEMPL/CMap::PLookup
- AFXTEMPL/CMap::RemoveAll
- AFXTEMPL/CMap::RemoveKey
- AFXTEMPL/CMap::SetAt
dev_langs:
- C++
helpviewer_keywords:
- dictionary mapping class
- collection classes, dictionary mapping
- CMap class
ms.assetid: 640a45ab-0993-4def-97ec-42cc78eb10b9
caps.latest.revision: 24
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
ms.openlocfilehash: 680d44fe6154861d2c638697cfc9d3fbeab36cc4
ms.lasthandoff: 02/24/2017

---
# <a name="cmap-class"></a>CMap 類別
字典集合類別，這個類別會將唯一索引鍵對應至值。  
  
## <a name="syntax"></a>語法  
  
```  
template<class KEY, class ARG_KEY, class VALUE, class ARG_VALUE>class CMap : public CObject  
```  
  
#### <a name="parameters"></a>參數  
 `KEY`  
 做為索引鍵的對應物件的類別。  
  
 `ARG` *_* `KEY`  
 資料型別用於`KEY`引數; 通常參考`KEY`。  
  
 `VALUE`  
 儲存在對應中的物件類別。  
  
 `ARG` *_* `VALUE`  
 資料型別用於`VALUE`引數; 通常參考`VALUE`。  
  
## <a name="members"></a>Members  
  
### <a name="public-structures"></a>公用結構  
  
|名稱|說明|  
|----------|-----------------|  
|[CMap::CPair](#cpair)|巢狀的結構，其中包含的索引鍵值和相關聯的物件的值。|  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMap::CMap](#cmap)|建構對應索引鍵與值的集合。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMap::GetCount](#getcount)|傳回這個對應中的項目數目。|  
|[CMap::GetHashTableSize](#gethashtablesize)|傳回雜湊表中的項目數目。|  
|[CMap::GetNextAssoc](#getnextassoc)|取得逐一查看下一個項目。|  
|[CMap::GetSize](#getsize)|傳回這個對應中的項目數目。|  
|[CMap::GetStartPosition](#getstartposition)|傳回第一個項目的位置。|  
|[CMap::InitHashTable](#inithashtable)|初始化雜湊表，並指定其大小。|  
|[CMap::IsEmpty](#isempty)|測試空白對應條件 （沒有項目）。|  
|[CMap::Lookup](#lookup)|查閱對應至指定的索引鍵的值。|  
|[CMap::PGetFirstAssoc](#pgetfirstassoc)|傳回的第一個元素的指標。|  
|[CMap::PGetNextAssoc](#pgetnextassoc)|逐一查看的指標取得下一個項目。|  
|[CMap::PLookup](#plookup)|傳回其值符合指定的值的索引鍵的指標。|  
|[CMap::RemoveAll](#removeall)|此對應會移除所有項目。|  
|[CMap::RemoveKey](#removekey)|移除索引鍵所指定的項目。|  
|[CMap::SetAt](#setat)|將項目插入對應中。如果找到相符的索引鍵，會取代現有的項目。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CMap::operator]](#operator_at)|將項目插入對應 â €"運算子替代`SetAt`。|  
  
## <a name="remarks"></a>備註  
 一旦您已插入對應的索引鍵 / 值組 （項目），您就可以有效率地擷取，或刪除使用金鑰來存取它的組。 您也可以逐一對應中的所有項目。  
  
 型別的變數**位置**用於替代的存取權的項目。 您可以使用**位置**「 記住 」 項目，並逐一對應。 您可能會認為這個反覆項目是循序的索引鍵的值。不存在。 擷取項目的順序是不確定的。  
  
 全域 helper 函式，這個類別呼叫的特定成員函式必須是可自訂的大部分的使用`CMap`類別。 請參閱[集合類別 Helper](../../mfc/reference/collection-class-helpers.md)巨集和全域變數 部分中`MFC``Reference`。  
  
 `CMap`覆寫[CObject::Serialize](../../mfc/reference/cobject-class.md#serialize)支援序列化和傾印的項目。 如果對應儲存至封存使用`Serialize`，每個地圖元素會依序序列化。 預設實作`SerializeElements`helper 函式功能的位元寫入。 資訊的指標集合項目序列化衍生自`CObject`或其他使用者定義型別，請參閱[How to︰ 建立類型安全集合](../../mfc/how-to-make-a-type-safe-collection.md)。  
  
 如果您需要對應 （索引鍵和值） 中的個別項目診斷傾印，您必須設定為 1 或更高的傾印內容的深度。  
  
 當`CMap`物件被刪除，或其項目移除時，會移除索引鍵和值。  
  
 Map 類別的衍生是類似於清單衍生。 請參閱文章[集合](../../mfc/collections.md)的特殊用途的清單類別衍生的範例。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMap`  
  
## <a name="requirements"></a>需求  
 **Header:** afxtempl.h  
  
##  <a name="cmap"></a>CMap::CMap  
 建構空的對應。  
  
```  
CMap(INT_PTR nBlockSize = 10);
```  
  
### <a name="parameters"></a>參數  
 `nBlockSize`  
 指定用於擴充對應的記憶體配置資料粒度。  
  
### <a name="remarks"></a>備註  
 隨著對應時，記憶體配置單位的`nBlockSize`項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&56;](../../mfc/codesnippet/cpp/cmap-class_1.cpp)]  
  
##  <a name="cpair"></a>CMap::CPair  
 包含索引鍵的值和相關聯的物件的值。  
  
### <a name="remarks"></a>備註  
 這是在類別內的巢狀的結構[CMap](../../mfc/reference/cmap-class.md)。  
  
 結構是由兩個欄位所組成︰  
  
- **keyÂ Â Â**索引鍵類型的實際值。  
  
- **valueÂ Â Â**相關聯的物件的值。  
  
 它用來儲存傳回的值[CMap::PLookup](#plookup)， [CMap::PGetFirstAssoc](#pgetfirstassoc)，和[CMap::PGetNextAssoc](#pgetnextassoc)。  
  
### <a name="example"></a>範例  
 如需使用方式的範例，請參閱範例[CMap::PLookup](#plookup)。  
  
##  <a name="getcount"></a>CMap::GetCount  
 擷取對應中的項目數。  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 元素數。  
  
### <a name="example"></a>範例  
 請參閱範例[CMap::Lookup](#lookup)。  
  
##  <a name="gethashtablesize"></a>CMap::GetHashTableSize  
 決定在對應的雜湊表中的項目數。  
  
```  
UINT GetHashTableSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 雜湊表中的項目數目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&57;](../../mfc/codesnippet/cpp/cmap-class_2.cpp)]  
  
##  <a name="getnextassoc"></a>CMap::GetNextAssoc  
 擷取對應的項目在`rNextPosition`，然後更新`rNextPosition`來指向對應中的下一個項目。  
  
```  
void GetNextAssoc(
    POSITION& rNextPosition,
    KEY& rKey,
    VALUE& rValue) const;  
```  
  
### <a name="parameters"></a>參數  
 `rNextPosition`  
 指定的參考**位置**前一個傳回值`GetNextAssoc`或`GetStartPosition`呼叫。  
  
 *索引鍵*  
 指定對應的索引鍵的類型樣板參數。  
  
 `rKey`  
 指定傳回的索引鍵的擷取的項目。  
  
 *值*  
 指定的對應值的類型樣板參數。  
  
 `rValue`  
 指定擷取的項目傳回的值。  
  
### <a name="remarks"></a>備註  
 此函式是最適合用來逐一查看對應中的所有項目。 請注意，位置順序不一定與索引鍵值順序相同。  
  
 如果擷取的項目是在對應中，最後則新值`rNextPosition`設為**NULL**。  
  
### <a name="example"></a>範例  
 請參閱範例[CMap::SetAt](#setat)。  
  
##  <a name="getsize"></a>CMap::GetSize  
 傳回對應的項目數目。  
  
```  
INT_PTR GetSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 在對應中的項目數目。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來擷取對應中的項目數。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&58;](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]  
  
##  <a name="getstartposition"></a>CMap::GetStartPosition  
 一開始會傳回對應的反覆項目**位置**值傳遞至`GetNextAssoc`呼叫。  
  
```  
POSITION GetStartPosition() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A**位置**值，指出對應; 上逐一查看的開始位置或**NULL**如果對應是空的。  
  
### <a name="remarks"></a>備註  
 反覆項目序列不是可預測的因此，「 第一個項目在對應中的 」 有任何特殊意義。  
  
### <a name="example"></a>範例  
 請參閱範例[CMap::SetAt](#setat)。  
  
##  <a name="inithashtable"></a>CMap::InitHashTable  
 初始化雜湊表。  
  
```  
void InitHashTable(UINT hashSize, BOOL  bAllocNow = TRUEÂ);  
```  
  
### <a name="parameters"></a>參數  
 `hashSize`  
 雜湊表中的項目數。  
  
 `bAllocNow`  
 如果**TRUE**，配置的雜湊表，在啟動時，必要時，否則配置表格。  
  
### <a name="remarks"></a>備註  
 為了達到最佳效能，雜湊資料表大小應該是質數。 若要衝突降到最低，大小應該大約 20%超過最大預期的資料集。  
  
### <a name="example"></a>範例  
 請參閱範例[CMap::Lookup](#lookup)。  
  
##  <a name="isempty"></a>CMap::IsEmpty  
 決定是否是空的對應。  
  
```  
BOOL IsEmpty() const;  
```  
  
### <a name="return-value"></a>傳回值  
 此對應會不包含任何項目; 如果為非零否則為 0。  
  
### <a name="example"></a>範例  
 請參閱範例[CMap::RemoveAll](#removeall)。  
  
##  <a name="lookup"></a>CMap::Lookup  
 查閱對應至指定的索引鍵的值。  
  
```  
BOOL Lookup(ARG_KEY key, VALUE& rValue) const;  
```  
  
### <a name="parameters"></a>參數  
 `ARG_KEY`  
 指定的類型樣板參數`key`值。  
  
 `key`  
 指定識別的項目是要查閱的索引鍵。  
  
 *值*  
 指定要查閱之值的類型。  
  
 `rValue`  
 接收查詢最多值。  
  
### <a name="return-value"></a>傳回值  
 非零，如果找不到項目。否則為 0。  
  
### <a name="remarks"></a>備註  
 `Lookup`若要快速尋找符合您指定的索引鍵的索引鍵的對應項目，會使用雜湊演算法。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&58;](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]  
  
##  <a name="operator_at"></a>CMap::operator]  
 方便的替代`SetAt`成員函式。  
  
```  
VALUE& operator[](arg_key key);
```  
  
### <a name="parameters"></a>參數  
 *值*  
 樣板參數指定類型的對應值。  
  
 `ARG_KEY`  
 指定的索引鍵值的類型樣板參數。  
  
 `key`  
 用來擷取值，從對應的金鑰。  
  
### <a name="remarks"></a>備註  
 因此它可以用於只在指派陳述式 (l-value) 的左側。 如果沒有具有指定之索引鍵的對應項目，則會建立新的項目。  
  
 任何 「 右側 」 （右值） 相當於這個運算子因為沒有索引鍵在對應中找到的可能性。 使用`Lookup`項目擷取的成員函式。  
  
### <a name="example"></a>範例  
 請參閱範例[CMap::Lookup](#lookup)。  
  
##  <a name="pgetfirstassoc"></a>CMap::PGetFirstAssoc  
 傳回對應物件的第一個項目。  
  
```  
const CPair* PGetFirstAssoc() const;Â CPair* PGetFirstAssoc();  
```  
  
### <a name="return-value"></a>傳回值  
 指向對應; 中的第一個項目請參閱[CMap::CPair](#cpair)。 如果對應不包含任何項目，這個值是**NULL**。  
  
### <a name="remarks"></a>備註  
 呼叫此函式指標的第一個項目傳回 map 物件中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&59;](../../mfc/codesnippet/cpp/cmap-class_4.cpp)]  
  
##  <a name="pgetnextassoc"></a>CMap::PGetNextAssoc  
 擷取所指的對應項目`pAssocRec`。  
  
```  
const CPair *PGetNextAssoc(const CPair* pAssocRet) const;  
  
CPair *PGetNextAssoc(const CPair* pAssocRet);
```  
  
### <a name="parameters"></a>參數  
 *pAssocRet*  
 前一個對應項目會指向[PGetNextAssoc](#pgetnextassoc)或[CMap::PGetFirstAssoc](#pgetfirstassoc)呼叫。  
  
### <a name="return-value"></a>傳回值  
 指向對應; 中的下一個項目請參閱[CMap::CPair](#cpair)。 如果項目是在對應中的最後一個，這個值是**NULL**。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來逐一查看對應中的所有項目。 擷取第一個項目，藉由呼叫`PGetFirstAssoc`，然後逐一連續呼叫來對應`PGetNextAssoc`。  
  
### <a name="example"></a>範例  
 請參閱範例[CMap::PGetFirstAssoc](#pgetfirstassoc)。  
  
##  <a name="plookup"></a>CMap::PLookup  
 尋找對應至指定的索引鍵的值。  
  
```  
const CPair* PLookup(ARG_KEY  key) const;
CPair* PLookup(Â    ARG_KEY  keyÂ);  ```  
  
### Parameters  
 `key`  
 Key for the element to be searched for.  
  
### Return Value  
 A pointer to a key structure; see [CMap::CPair](#cpair). If no match is found, `CMap::PLookup` returns `NULL`.  
  
### Remarks  
 Call this method to search for a map element with a key that exactly matches the given key.  
  
### Example  
 [!code-cpp[NVC_MFCCollections#60](../../mfc/codesnippet/cpp/cmap-class_5.cpp)]  
  
##  <a name="removeall"></a>  CMap::RemoveAll  
 Removes all the values from this map by calling the global helper function **DestructElements**.  
  
```  
void RemoveAll();
```  
  
### Remarks  
 The function works correctly if the map is already empty.  
  
### Example  
 [!code-cpp[NVC_MFCCollections#61](../../mfc/codesnippet/cpp/cmap-class_6.cpp)]  
  
##  <a name="removekey"></a>  CMap::RemoveKey  
 Looks up the map entry corresponding to the supplied key; then, if the key is found, removes the entry.  
  
```  
BOOL RemoveKey(ARG_KEY key);
```  
  
### Parameters  
 `ARG_KEY`  
 Template parameter specifying the type of the key.  
  
 `key`  
 Key for the element to be removed.  
  
### Return Value  
 Nonzero if the entry was found and successfully removed; otherwise 0.  
  
### Remarks  
 The **DestructElements** helper function is used to remove the entry.  
  
### Example  
 See the example for [CMap::SetAt](#setat).  
  
##  <a name="setat"></a>  CMap::SetAt  
 The primary means to insert an element in a map.  
  
```  
void SetAt (ARG_KEY 索引鍵的 ARG_VALUE newValue;)
```  
  
### Parameters  
 `ARG_KEY`  
 Template parameter specifying the type of the `key` parameter.  
  
 `key`  
 Specifies the key of the new element.  
  
 `ARG_VALUE`  
 Template parameter specifying the type of the `newValue` parameter.  
  
 `newValue`  
 Specifies the value of the new element.  
  
### Remarks  
 First, the key is looked up. If the key is found, then the corresponding value is changed; otherwise a new key-value pair is created.  
  
### Example  
 [!code-cpp[NVC_MFCCollections#62](../../mfc/codesnippet/cpp/cmap-class_7.cpp)]  
  
## See Also  
 [MFC Sample COLLECT](../../visual-cpp-samples.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Hierarchy Chart](../../mfc/hierarchy-chart.md)  


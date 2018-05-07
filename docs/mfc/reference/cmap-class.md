---
title: CMap 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- CMap [MFC], CPair
- CMap [MFC], CMap
- CMap [MFC], GetCount
- CMap [MFC], GetHashTableSize
- CMap [MFC], GetNextAssoc
- CMap [MFC], GetSize
- CMap [MFC], GetStartPosition
- CMap [MFC], InitHashTable
- CMap [MFC], IsEmpty
- CMap [MFC], Lookup
- CMap [MFC], PGetFirstAssoc
- CMap [MFC], PGetNextAssoc
- CMap [MFC], PLookup
- CMap [MFC], RemoveAll
- CMap [MFC], RemoveKey
- CMap [MFC], SetAt
ms.assetid: 640a45ab-0993-4def-97ec-42cc78eb10b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 19b9c25659938e049807eb4e4b41dafd51ebe8e9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cmap-class"></a>CMap 類別
字典集合類別，這個類別會將唯一索引鍵對應至值。  
  
## <a name="syntax"></a>語法  
  
```  
template<class KEY, class ARG_KEY, class VALUE, class ARG_VALUE>class CMap : public CObject  
```  
  
#### <a name="parameters"></a>參數  
 `KEY`  
 做為索引鍵對應的物件類別。  
  
 `ARG` *_* `KEY`  
 資料型別用於`KEY`引數; 通常參考`KEY`。  
  
 `VALUE`  
 儲存在 map 中的物件類別。  
  
 `ARG` *_* `VALUE`  
 資料型別用於`VALUE`引數; 通常參考`VALUE`。  
  
## <a name="members"></a>成員  
  
### <a name="public-structures"></a>公用結構  
  
|名稱|描述|  
|----------|-----------------|  
|[CMap::CPair](#cpair)|巢狀的結構，包含索引鍵的值，以及相關聯之物件的值。|  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMap::CMap](#cmap)|建構將索引鍵對應至值的集合。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMap::GetCount](#getcount)|在此對應中傳回的項目數。|  
|[CMap::GetHashTableSize](#gethashtablesize)|傳回雜湊表中的項目數目。|  
|[CMap::GetNextAssoc](#getnextassoc)|取得逐一查看下一個項目。|  
|[CMap::GetSize](#getsize)|在此對應中傳回的項目數。|  
|[CMap::GetStartPosition](#getstartposition)|傳回第一個項目的位置。|  
|[CMap::InitHashTable](#inithashtable)|初始化雜湊表，並指定其大小。|  
|[CMap::IsEmpty](#isempty)|測試的空白對應條件 （沒有項目）。|  
|[CMap::Lookup](#lookup)|查閱對應到指定的索引鍵的值。|  
|[CMap::PGetFirstAssoc](#pgetfirstassoc)|讓指標回到第一個項目。|  
|[CMap::PGetNextAssoc](#pgetnextassoc)|取得下一個項目指標來反覆查看。|  
|[CMap::PLookup](#plookup)|傳回其值符合指定的值的索引鍵的指標。|  
|[CMap::RemoveAll](#removeall)|此對應中移除所有項目。|  
|[CMap::RemoveKey](#removekey)|移除索引鍵所指定的項目。|  
|[CMap::SetAt](#setat)|將項目插入對應中。如果找到相符的索引鍵，會取代現有的項目。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CMap::operator]](#operator_at)|將項目插入對應 — 運算子替代`SetAt`。|  
  
## <a name="remarks"></a>備註  
 一旦您已插入對應的索引鍵-值組 （項目），您就可以有效率地擷取，或刪除使用可以存取它的金鑰組。 您也可以逐一查看對應中的所有項目。  
  
 類型的變數**位置**用於替代來存取項目。 您可以使用**位置**「 記住 」 項目並逐一查看對應。 您可能會認為這個反覆項目是循序的索引鍵值;不存在。 擷取項目的順序皆不明確。  
  
 全域 helper 函式，這個類別呼叫的特定成員函式必須是可自訂的大部分的使用`CMap`類別。 請參閱[集合類別 Helper](../../mfc/reference/collection-class-helpers.md)的巨集和全域節`MFC Reference`。  
  
 `CMap` 覆寫[cobject:: Serialize](../../mfc/reference/cobject-class.md#serialize)支援序列化和傾印的項目。 如果對應會儲存至封存使用`Serialize`，每個地圖元素會依次序列化。 預設實作`SerializeElements`helper 函式沒有位元的寫入。 如需序列化的指標集合的項目資訊衍生自`CObject`或其他使用者定義型別，請參閱[如何： 建立類型安全集合](../../mfc/how-to-make-a-type-safe-collection.md)。  
  
 如果您需要個別的項目對應 （索引鍵和值） 中的診斷傾印，您必須設定為 1 或更大的傾印內容的深度。  
  
 當`CMap`物件被刪除，或當其項目會遭到移除，會移除索引鍵和值。  
  
 清單衍生相似的對應類別衍生。 請參閱文章[集合](../../mfc/collections.md)取得的特殊用途的清單類別衍生的說明。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMap`  
  
## <a name="requirements"></a>需求  
 **Header:** afxtempl.h  
  
##  <a name="cmap"></a>  CMap::CMap  
 建構空的對應。  
  
```  
CMap(INT_PTR nBlockSize = 10);
```  
  
### <a name="parameters"></a>參數  
 `nBlockSize`  
 指定擴充對應的記憶體配置資料粒的度。  
  
### <a name="remarks"></a>備註  
 記憶體對應成長時，配置單位的`nBlockSize`項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections#56](../../mfc/codesnippet/cpp/cmap-class_1.cpp)]  
  
##  <a name="cpair"></a>  CMap::CPair  
 包含索引鍵的值和相關聯之物件的值。  
  
### <a name="remarks"></a>備註  
 這是在類別內的巢狀的結構[CMap](../../mfc/reference/cmap-class.md)。  
  
 結構是由兩個欄位所組成：  
  
- **索引鍵**索引鍵類型的實際值。  
  
- **值**相關聯之物件的值。  
  
 它用來儲存傳回的值[CMap::PLookup](#plookup)， [CMap::PGetFirstAssoc](#pgetfirstassoc)，和[CMap::PGetNextAssoc](#pgetnextassoc)。  
  
### <a name="example"></a>範例  
 如需使用方式的範例，請參閱範例的[CMap::PLookup](#plookup)。  
  
##  <a name="getcount"></a>  CMap::GetCount  
 擷取在對應中的項目數。  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 元素數。  
  
### <a name="example"></a>範例  
 請參閱範例的[CMap::Lookup](#lookup)。  
  
##  <a name="gethashtablesize"></a>  CMap::GetHashTableSize  
 決定在對應的雜湊資料表中的項目數。  
  
```  
UINT GetHashTableSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 雜湊表中的元素數目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections#57](../../mfc/codesnippet/cpp/cmap-class_2.cpp)]  
  
##  <a name="getnextassoc"></a>  CMap::GetNextAssoc  
 擷取位於的地圖元素`rNextPosition`，然後更新`rNextPosition`指向對應中的下一個項目。  
  
```  
void GetNextAssoc(
    POSITION& rNextPosition,
    KEY& rKey,
    VALUE& rValue) const;  
```  
  
### <a name="parameters"></a>參數  
 `rNextPosition`  
 指定的參考**位置**傳回先前值`GetNextAssoc`或`GetStartPosition`呼叫。  
  
 *KEY*  
 指定地圖的索引鍵的類型樣板參數。  
  
 `rKey`  
 指定傳回的索引鍵的擷取的項目。  
  
 *值*  
 指定的對應值的類型樣板參數。  
  
 `rValue`  
 指定的擷取的項目傳回的值。  
  
### <a name="remarks"></a>備註  
 此函式是最適合用來逐一查看對應中的所有項目。 請注意，位置順序不一定與索引鍵值順序相同。  
  
 如果擷取的項目是在對應中，最後則新值`rNextPosition`設**NULL**。  
  
### <a name="example"></a>範例  
 請參閱範例的[CMap::SetAt](#setat)。  
  
##  <a name="getsize"></a>  CMap::GetSize  
 傳回地圖元素的數目。  
  
```  
INT_PTR GetSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 在對應中的項目數目。  
  
### <a name="remarks"></a>備註  
 呼叫此方法以擷取在對應中的項目數。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]  
  
##  <a name="getstartposition"></a>  CMap::GetStartPosition  
 啟動對應反覆項目，藉由傳回**位置**可以傳遞至值`GetNextAssoc`呼叫。  
  
```  
POSITION GetStartPosition() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A**位置**值，指出逐一查看對應的開始位置或**NULL**如果 map 是空的。  
  
### <a name="remarks"></a>備註  
 反覆項目順序不是可預測;因此，「 第一個項目在對應 」 有沒有特殊的意義。  
  
### <a name="example"></a>範例  
 請參閱範例的[CMap::SetAt](#setat)。  
  
##  <a name="inithashtable"></a>  CMap::InitHashTable  
 初始化雜湊表。  
  
```  
void InitHashTable(UINT hashSize, BOOL  bAllocNow = TRUE);  
```  
  
### <a name="parameters"></a>參數  
 `hashSize`  
 雜湊表中的項目數。  
  
 `bAllocNow`  
 如果**TRUE**，配置雜湊表初始化，在需要時，否則配置資料表。  
  
### <a name="remarks"></a>備註  
 為了達到最佳效能，雜湊資料表大小應該是質數。 衝突降到最低，大小應大約 20%超過最大預期的資料集。  
  
### <a name="example"></a>範例  
 請參閱範例的[CMap::Lookup](#lookup)。  
  
##  <a name="isempty"></a>  CMap::IsEmpty  
 決定地圖是否為空白。  
  
```  
BOOL IsEmpty() const;  
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果這個對應不包含任何項目。否則便是 0。  
  
### <a name="example"></a>範例  
 請參閱範例的[CMap::RemoveAll](#removeall)。  
  
##  <a name="lookup"></a>  CMap::Lookup  
 查閱對應到指定的索引鍵的值。  
  
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
 接收的總查閱值。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果找不到項目。否則便是 0。  
  
### <a name="remarks"></a>備註  
 `Lookup` 若要快速尋找完全符合指定的索引鍵的索引鍵的地圖元素，會使用雜湊演算法。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]  
  
##  <a name="operator_at"></a>  CMap::operator]  
 能方便替代`SetAt`成員函式。  
  
```  
VALUE& operator[](arg_key key);
```  
  
### <a name="parameters"></a>參數  
 *值*  
 指定的對應值類型的樣板參數。  
  
 `ARG_KEY`  
 指定的索引鍵值的類型樣板參數。  
  
 `key`  
 索引鍵，用來擷取對應的值。  
  
### <a name="remarks"></a>備註  
 因此可以使用只在指派陳述式 （左值） 的左半部。 如果沒有具有指定之索引鍵的對應項目，則會建立新的項目。  
  
 沒有任何 「 右邊 」 （右值） 相當於這個運算子因為索引鍵找到對應中可能發生。 使用`Lookup`項目擷取的成員函式。  
  
### <a name="example"></a>範例  
 請參閱範例的[CMap::Lookup](#lookup)。  
  
##  <a name="pgetfirstassoc"></a>  CMap::PGetFirstAssoc  
 傳回對應物件的第一個項目。  
  
```  
const CPair* PGetFirstAssoc() const; 
CPair* PGetFirstAssoc();  
```  
  
### <a name="return-value"></a>傳回值  
 指向對應中的第一個項目請參閱[CMap::CPair](#cpair)。 如果對應不包含任何項目，這個值是**NULL**。  
  
### <a name="remarks"></a>備註  
 呼叫此函式可傳回指標 map 物件中的第一個項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections#59](../../mfc/codesnippet/cpp/cmap-class_4.cpp)]  
  
##  <a name="pgetnextassoc"></a>  CMap::PGetNextAssoc  
 擷取所指的地圖元素`pAssocRec`。  
  
```  
const CPair *PGetNextAssoc(const CPair* pAssocRet) const;  
  
CPair *PGetNextAssoc(const CPair* pAssocRet);
```  
  
### <a name="parameters"></a>參數  
 *pAssocRet*  
 傳回先前的對應項目會指向[PGetNextAssoc](#pgetnextassoc)或[CMap::PGetFirstAssoc](#pgetfirstassoc)呼叫。  
  
### <a name="return-value"></a>傳回值  
 指向對應中的下一個項目請參閱[CMap::CPair](#cpair)。 如果項目，則對應中的最後一個，這個值是**NULL**。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來逐一查看對應中的所有項目。 擷取第一個項目，藉由呼叫`PGetFirstAssoc`，然後逐一因為連續呼叫來對應`PGetNextAssoc`。  
  
### <a name="example"></a>範例  
 請參閱範例的[CMap::PGetFirstAssoc](#pgetfirstassoc)。  
  
##  <a name="plookup"></a>  CMap::PLookup  
 尋找對應到指定的索引鍵的值。  
  
```  
const CPair* PLookup(ARG_KEY key) const;
CPair* PLookup(ARG_KEY key);  
```  
  
### <a name="parameters"></a>參數  
 `key`  
 要搜尋的項目索引鍵。  
  
### <a name="return-value"></a>傳回值  
 指向的索引鍵的結構。請參閱[CMap::CPair](#cpair)。 如果找到相符項目，`CMap::PLookup`傳回`NULL`。  
  
### <a name="remarks"></a>備註  
 呼叫此方法以使用完全符合指定的索引鍵的索引鍵的地圖元素的搜尋。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections#60](../../mfc/codesnippet/cpp/cmap-class_5.cpp)]  
  
##  <a name="removeall"></a>  CMap::RemoveAll  
 移除此對應中的所有值，藉由呼叫全域 helper 函式**DestructElements**。  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>備註  
 如果已經是空的對應函式可正確運作。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections#61](../../mfc/codesnippet/cpp/cmap-class_6.cpp)]  
  
##  <a name="removekey"></a>  CMap::RemoveKey  
 查閱對應項目對應到提供的索引鍵。然後，如果找到機碼，移除項目。  
  
```  
BOOL RemoveKey(ARG_KEY key);
```  
  
### <a name="parameters"></a>參數  
 `ARG_KEY`  
 指定索引鍵的類型樣板參數。  
  
 `key`  
 要移除的項目索引鍵。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果找到，已成功移除項目否則便是 0。  
  
### <a name="remarks"></a>備註  
 **DestructElements** helper 函式用來移除的項目。  
  
### <a name="example"></a>範例  
 請參閱範例的[CMap::SetAt](#setat)。  
  
##  <a name="setat"></a>  CMap::SetAt  
 主要的方法將項目插入對應中。  
  
```  
void SetAt(ARG_KEY key, ARG_VALUE newValue);
```  
  
### <a name="parameters"></a>參數  
 `ARG_KEY`  
 指定的類型樣板參數`key`參數。  
  
 `key`  
 指定新項目的索引鍵。  
  
 `ARG_VALUE`  
 指定的類型樣板參數`newValue`參數。  
  
 `newValue`  
 指定新項目的值。  
  
### <a name="remarks"></a>備註  
 首先，索引鍵查詢。 如果找到索引鍵，則對應的值變更時。否則會建立新的索引鍵-值組。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections#62](../../mfc/codesnippet/cpp/cmap-class_7.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例收集](../../visual-cpp-samples.md)   
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)  

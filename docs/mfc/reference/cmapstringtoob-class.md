---
title: "CMapStringToOb 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMapStringToOb
- AFXCOLL/CMapStringToOb
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
- collection classes, string mapping
- CMapStringToOb class
- strings [C++], class for mapping
ms.assetid: 09653980-b885-4f3a-8594-0aeb7f94c601
caps.latest.revision: 20
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 2bfd277ebc1f00784d8e3d9686623777cb7fb5a5
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cmapstringtoob-class"></a>CMapStringToOb 類別
字典集合類別，這個類別會將唯一的 `CString` 物件對應至 `CObject` 指標。  
  
## <a name="syntax"></a>語法  
  
```  
class CMapStringToOb : public CObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMapStringToOb::CMapStringToOb](#cmapstringtoob)|建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMapStringToOb::GetCount](#getcount)|傳回這個對應中的項目數目。|  
|[CMapStringToOb::GetHashTableSize](#gethashtablesize)|判斷目前的雜湊表中的元素數目。|  
|[CMapStringToOb::GetNextAssoc](#getnextassoc)|取得逐一查看下一個項目。|  
|[CMapStringToOb::GetSize](#getsize)|傳回這個對應中的項目數目。|  
|[CMapStringToOb::GetStartPosition](#getstartposition)|傳回第一個項目的位置。|  
|[CMapStringToOb::HashKey](#hashkey)|計算指定之索引鍵的雜湊值。|  
|[CMapStringToOb::InitHashTable](#inithashtable)|初始化雜湊表。|  
|[CMapStringToOb::IsEmpty](#isempty)|測試空白對應條件 （沒有項目）。|  
|[CMapStringToOb::Lookup](#lookup)|查閱根據 void 指標索引鍵的 void 指標。 指標值，而不將它所指向，實體用於索引鍵的比較。|  
|[CMapStringToOb::LookupKey](#lookupkey)|傳回指定之索引鍵值相關聯的索引鍵的參考。|  
|[CMapStringToOb::RemoveAll](#removeall)|此對應會移除所有項目。|  
|[CMapStringToOb::RemoveKey](#removekey)|移除索引鍵所指定的項目。|  
|[CMapStringToOb::SetAt](#setat)|將項目插入對應中。如果找到相符的索引鍵，會取代現有的項目。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CMapStringToOb::operator]](#operator_at)|將項目插入對應 — 運算子替代`SetAt`。|  
  
## <a name="remarks"></a>備註  
 一旦您已插入`CString` -  `CObject*`組 （項目） 加入至對應，可以有效率地擷取或刪除對使用字串或`CString`做為索引鍵的值。 您也可以逐一對應中的所有項目。  
  
 型別的變數**位置**適用於所有對應變化的替代項目存取權。 您可以使用**位置**「 記住 」 項目，並逐一對應。 您可能會認為這個反覆項目是循序的索引鍵的值。不存在。 擷取項目的順序是不確定的。  
  
 `CMapStringToOb` 引入 `IMPLEMENT_SERIAL` 巨集，以支援其項目的序列化和傾印。 如果對應儲存至封存檔，多載的插入與每個項目會依次序列化 ( ** << **) 運算子或`Serialize`成員函式。  
  
 如果您需要在對應中的個別項目診斷傾印 (`CString`值和`CObject`內容)，您必須將傾印內容的深度設定為大於或等於 1。  
  
 當`CMapStringToOb`物件被刪除，或當其項目被移除，`CString`物件和`CObject`會移除指標。 所參考的物件`CObject`指標不會終結。  
  
 Map 類別的衍生是類似於清單衍生。 請參閱文章[集合](../../mfc/collections.md)的特殊用途的清單類別衍生的範例。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMapStringToOb`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxcoll.h  
  
##  <a name="cmapstringtoob"></a>CMapStringToOb::CMapStringToOb  
 建構空`CString`-到-`CObject*`對應。  
  
```  
CMapStringToOb(INT_PTR nBlockSize = 10);
```  
  
### <a name="parameters"></a>參數  
 `nBlockSize`  
 指定用於擴充對應的記憶體配置資料粒度。  
  
### <a name="remarks"></a>備註  
 隨著對應時，記憶體配置單位的`nBlockSize`項目。  
  
 下表顯示的其他成員函式，類似於**CMapStringToOb:: CMapStringToOb**。  
  
|類別|成員函式|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**CMapPtrToPtr (INT_PTR** `nBlockSize` **= 10)。**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**CMapPtrToWord (INT_PTR** `nBlockSize` **= 10)。**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**CMapStringToPtr (INT_PTR** `nBlockSize` **= 10)。**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CMapStringToString (INT_PTR** `nBlockSize` **= 10)。**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CMapWordToOb (INT_PTR** `nBlockSize` **= 10)。**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**MapWordToPtr (INT_PTR** `nBlockSize` **= 10)。**|  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&63;](../../mfc/codesnippet/cpp/cmapstringtoob-class_1.cpp)]  
  
 請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)的清單`CAge`所有集合範例中使用的類別。  
  
##  <a name="getcount"></a>CMapStringToOb::GetCount  
 決定在對應中項目數目。  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 此對應中項目的數目。  
  
### <a name="remarks"></a>備註  
 下表顯示的其他成員函式，類似於`CMapStringToOb::GetCount`。  
  
|類別|成員函式|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Const; 的 INT_PTR GetCount （)**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**Const; 的 INT_PTR GetCount （)**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**Const; 的 INT_PTR GetCount （)**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Const; 的 INT_PTR GetCount （)**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**Const; 的 INT_PTR GetCount （)**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**Const; 的 INT_PTR GetCount （)**|  
  
### <a name="example"></a>範例  
 請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)的清單`CAge`所有集合範例中使用的類別。  
  
 [!code-cpp[NVC_MFCCollections #&64;](../../mfc/codesnippet/cpp/cmapstringtoob-class_2.cpp)]  
  
##  <a name="gethashtablesize"></a>CMapStringToOb::GetHashTableSize  
 判斷目前的雜湊表中的元素數目。  
  
```  
UINT GetHashTableSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回雜湊表中的項目數目。  
  
### <a name="remarks"></a>備註  
 下表顯示的其他成員函式，類似於`CMapStringToOb::GetHashTableSize`。  
  
|類別|成員函式|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT （GetHashTableSize) const;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT （GetHashTableSize) const;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT （GetHashTableSize) const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**UINT （GetHashTableSize) const;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**UINT （GetHashTableSize) const;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**UINT （GetHashTableSize) const;**|  
  
##  <a name="getnextassoc"></a>CMapStringToOb::GetNextAssoc  
 擷取對應的項目在*rNextPosition*，然後更新*rNextPosition*來指向對應中的下一個項目。  
  
```  
void GetNextAssoc(
    POSITION& rNextPosition,  
    CString& rKey,  
    CObject*& rValue) const;  
```  
  
### <a name="parameters"></a>參數  
 *rNextPosition*  
 指定的參考**位置**前一個傳回值**GetNextAssoc**或**GetStartPosition**呼叫。  
  
 *rKey*  
 指定傳回的索引鍵的擷取的項目 （字串）。  
  
 *右值*  
 指定傳回的值的擷取的項目 ( **CObject**指標)。 如需有關此參數的詳細資訊，請參閱 < 備註 >。  
  
### <a name="remarks"></a>備註  
 此函式是最適合用來逐一查看對應中的所有項目。 請注意，位置順序不一定與索引鍵值順序相同。  
  
 如果擷取的項目是在對應中，最後則新值*rNextPosition*設為**NULL**。  
  
 如*右值*參數，確定您的物件類型轉型**CObject\*&**，這是編譯器的要求，如下列範例所示︰  
  
 [!code-cpp[NVC_MFCCollections #&65;](../../mfc/codesnippet/cpp/cmapstringtoob-class_3.cpp)]  
  
 這不是的則為 true **GetNextAssoc**範本為基礎的對應。  
  
 下表顯示的其他成員函式，類似於**CMapStringToOb::GetNextAssoc**。  
  
|類別|成員函式|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void GetNextAssoc( POSITION&** *rNextPosition* **, void\*&** *rKey* **, void\*&** *rValue* **) const;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void GetNextAssoc( POSITION&** *rNextPosition* **, void\*&** *rKey* **, WORD&** *rValue* **) const;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void GetNextAssoc (位置 i** *rNextPosition* **，CString i** *rKey* **，void\* & ** *右值* **) const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void GetNextAssoc (位置 i** *rNextPosition* **，CString i** *rKey* **，CString i** *右值* **) const;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void GetNextAssoc (位置 i** *rNextPosition* **，WORD i** *rKey* **，CObject\* & ** *右值* **) const;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void GetNextAssoc( POSITION&** *rNextPosition* **, WORD&** *rKey* **, void\*&** *rValue* **) const;**|  
  
### <a name="example"></a>範例  
 請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)的清單`CAge`所有集合範例中使用的類別。  
  
 [!code-cpp[NVC_MFCCollections #&66;](../../mfc/codesnippet/cpp/cmapstringtoob-class_4.cpp)]  
  
 此程式的結果如下所示︰  
  
 `Lisa : a CAge at $4724 11`  
  
 `Marge : a CAge at $47A8 35`  
  
 `Homer : a CAge at $4766 36`  
  
 `Bart : a CAge at $45D4 13`  
  
##  <a name="getsize"></a>CMapStringToOb::GetSize  
 傳回對應的項目數目。  
  
```  
INT_PTR GetSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 在對應中的項目數目。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來擷取對應中的項目數。  
  
 下表顯示的其他成員函式，類似於`CMapStringToOb::GetSize`。  
  
|類別|成員函式|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Const; 的 INT_PTR GetSize （)**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**Const; 的 INT_PTR GetSize （)**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**Const; 的 INT_PTR GetSize （)**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Const; 的 INT_PTR GetSize （)**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**Const; 的 INT_PTR GetSize （)**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**Const; 的 INT_PTR GetSize （)**|  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&67;](../../mfc/codesnippet/cpp/cmapstringtoob-class_5.cpp)]  
  
##  <a name="getstartposition"></a>CMapStringToOb::GetStartPosition  
 一開始會傳回對應的反覆項目**位置**值傳遞至`GetNextAssoc`呼叫。  
  
```  
POSITION GetStartPosition() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A**位置**值，指出對應; 上逐一查看的開始位置或**NULL**如果對應是空的。  
  
### <a name="remarks"></a>備註  
 反覆項目序列不是可預測的因此，「 第一個項目在對應中的 」 有任何特殊意義。  
  
 下表顯示的其他成員函式，類似於`CMapStringToOb::GetStartPosition`。  
  
|類別|成員函式|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**位置 （GetStartPosition) const;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**位置 （GetStartPosition) const;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**位置 （GetStartPosition) const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**位置 （GetStartPosition) const;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**位置 （GetStartPosition) const;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**位置 （GetStartPosition) const;**|  
  
### <a name="example"></a>範例  
 請參閱範例[CMapStringToOb::GetNextAssoc](#getnextassoc)。  
  
##  <a name="hashkey"></a>CMapStringToOb::HashKey  
 計算指定之索引鍵的雜湊值。  
  
```  
UINT HashKey(LPCTSTR key) const;  
```  
  
### <a name="parameters"></a>參數  
 `key`  
 雜湊值會計算索引鍵。  
  
### <a name="return-value"></a>傳回值  
 索引鍵的雜湊值  
  
### <a name="remarks"></a>備註  
 下表顯示的其他成員函式，類似於`CMapStringToOb::HashKey`。  
  
|類別|成員函式|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT HashKey (void\* ** `key` **) const;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT HashKey (void\* ** `key` **) const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**UINT HashKey (LPCTSTR** `key` **) const;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT HashKey (LPCTSTR** `key` **) const;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**UINT HashKey (WORD** `key` **) const;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**UINT HashKey (WORD** `key` **) const;**|  
  
##  <a name="inithashtable"></a>CMapStringToOb::InitHashTable  
 初始化雜湊表。  
  
```  
void InitHashTable(
    UINT hashSize,  
    BOOL bAllocNow = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `hashSize`  
 雜湊表中的項目數。  
  
 `bAllocNow`  
 如果**TRUE**，配置的雜湊表，在啟動時，必要時，否則配置表格。  
  
### <a name="remarks"></a>備註  
 為了達到最佳效能，雜湊資料表大小應該是質數。 若要衝突降到最低，大小應該大約 20%超過最大預期的資料集。  
  
 下表顯示的其他成員函式，類似於`CMapStringToOb::InitHashTable`。  
  
|類別|成員函式|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void InitHashTable (UINT** `hashSize` **，BOOL** `bAllocNow` **= TRUE);**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void InitHashTable (UINT** `hashSize` **，BOOL** `bAllocNow` **= TRUE);**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void InitHashTable (UINT** `hashSize` **，BOOL** `bAllocNow` **= TRUE);**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void InitHashTable (UINT** `hashSize` **，BOOL** `bAllocNow` **= TRUE);**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void InitHashTable (UINT** `hashSize` **，BOOL** `bAllocNow` **= TRUE);**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void InitHashTable (UINT** `hashSize` **，BOOL** `bAllocNow` **= TRUE);**|  
  
##  <a name="isempty"></a>CMapStringToOb::IsEmpty  
 決定是否是空的對應。  
  
```  
BOOL IsEmpty() const;  
```  
  
### <a name="return-value"></a>傳回值  
 此對應會不包含任何項目; 如果為非零否則為 0。  
  
### <a name="example"></a>範例  
 請參閱範例[RemoveAll](#removeall)。  
  
### <a name="remarks"></a>備註  
 下表顯示的其他成員函式，類似於**CMapStringToOb:: IsEmpty**。  
  
|類別|成員函式|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL IsEmpty （) const;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL IsEmpty （) const;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL IsEmpty （) const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL IsEmpty （) const;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL IsEmpty （) const;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL IsEmpty （) const;**|  
  
##  <a name="lookup"></a>CMapStringToOb::Lookup  
 傳回`CObject`指標根據`CString`值。  
  
```  
BOOL Lookup(
    LPCTSTR key,  
    CObject*& rValue) const;  
```  
  
### <a name="parameters"></a>參數  
 `key`  
 指定識別的項目是要查閱的字串索引鍵。  
  
 `rValue`  
 指定傳回的值看起來最多項目。  
  
### <a name="return-value"></a>傳回值  
 非零，如果找不到項目。否則為 0。  
  
### <a name="remarks"></a>備註  
 `Lookup`若要快速尋找完全符合的索引鍵的對應項目會使用雜湊演算法 (`CString`值)。  
  
 下表顯示的其他成員函式，類似於`CMapStringToOb::LookUp`。  
  
|類別|成員函式|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL Lookup( void\*** `key` **, void\*&** `rValue` **) const;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL Lookup( void\*** `key` **, WORD&** `rValue` **) const;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL Lookup( LPCTSTR** `key` **, void\*&** `rValue` **) const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL 查閱 (LPCTSTR** `key` **，CString i** `rValue` **) const;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL Lookup( WORD** `key` **, CObject\*&** `rValue` **) const;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL Lookup( WORD** `key` **, void\*&** `rValue` **) const;**|  
  
### <a name="example"></a>範例  
 請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)的清單`CAge`所有集合範例中使用的類別。  
  
 [!code-cpp[NVC_MFCCollections #&68;](../../mfc/codesnippet/cpp/cmapstringtoob-class_6.cpp)]  
  
##  <a name="lookupkey"></a>CMapStringToOb::LookupKey  
 傳回指定之索引鍵值相關聯的索引鍵的參考。  
  
```  
BOOL LookupKey(
    LPCTSTR key,  
    LPCTSTR& rKey) const;  
```  
  
### <a name="parameters"></a>參數  
 `key`  
 指定識別的項目是要查閱的字串索引鍵。  
  
 `rKey`  
 相關聯的索引鍵參考。  
  
### <a name="return-value"></a>傳回值  
 非零，如果找不到索引鍵。否則為 0。  
  
### <a name="remarks"></a>備註  
 如果使用從對應移除相關聯的項目之後，或已終結對應之後，會使用索引鍵參考並不安全。  
  
 下表顯示的其他成員函式，類似於**CMapStringToOb:: LookupKey**。  
  
|類別|成員函式|  
|-----------|---------------------|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL LookupKey (LPCTSTR** `key` **，LPCTSTR i** `rKey` **) const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL LookupKey (LPCTSTR** `key` **，LPCTSTR i** `rKey` **) const;**|  
  
##  <a name="operator_at"></a>CMapStringToOb::operator]  
 方便的替代`SetAt`成員函式。  
  
```  
CObject*& operator[ ](lpctstr key);
```  
  
### <a name="return-value"></a>傳回值  
 指標的參考`CObject`物件; 或**NULL**如果對應是空的或`key`超出範圍。  
  
### <a name="remarks"></a>備註  
 因此它可以用於只在指派陳述式 (l-value) 的左側。 如果沒有具有指定之索引鍵的對應項目，則會建立新的項目。  
  
 任何 「 右側 」 （右值） 相當於這個運算子因為沒有索引鍵在對應中找到的可能性。 使用`Lookup`項目擷取的成員函式。  
  
 下表顯示的其他成員函式，類似於**CMapStringToOb::operator []**。  
  
|類別|成員函式|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void\*& operator[](void\*** `key` **\);**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**WORD& operator[](void\*** `key` **\);**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void\*& operator[](lpctstr** `key` **\);**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CString i 運算子 [] (lpctstr** `key` ** \);**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CObject\*& operator[](word** `key` **\);**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void\*& operator[](word** `key` **\);**|  
  
### <a name="example"></a>範例  
 請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)的清單`CAge`所有集合範例中使用的類別。  
  
 [!code-cpp[NVC_MFCCollections #&72;](../../mfc/codesnippet/cpp/cmapstringtoob-class_7.cpp)]  
  
 此程式的結果如下所示︰  
  
 `Operator [] example: A CMapStringToOb with 2 elements`  
  
 `[Lisa] = a CAge at $4A02 11`  
  
 `[Bart] = a CAge at $497E 13`  
  
##  <a name="removeall"></a>CMapStringToOb::RemoveAll  
 此對應會移除所有項目，並終結`CString`索引鍵的物件。  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>備註  
 `CObject`每個索引鍵所參考的物件不會終結。 `RemoveAll`函式會導致記憶體流失，如果您不會確定可參考`CObject`會終結物件。  
  
 如果已經是空的對應函式的運作正常。  
  
 下表顯示的其他成員函式，類似於`CMapStringToOb::RemoveAll`。  
  
|類別|成員函式|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void RemoveAll （);**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void RemoveAll （);**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void RemoveAll （);**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void RemoveAll （);**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void RemoveAll （);**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void RemoveAll （);**|  
  
### <a name="example"></a>範例  
 請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)的清單`CAge`所有集合範例中使用的類別。  
  
 [!code-cpp[NVC_MFCCollections #&69;](../../mfc/codesnippet/cpp/cmapstringtoob-class_8.cpp)]  
  
##  <a name="removekey"></a>CMapStringToOb::RemoveKey  
 提供索引鍵對應的對應項目查詢然後，如果找到索引鍵，則移除的項目。  
  
```  
BOOL RemoveKey(LPCTSTR key);
```  
  
### <a name="parameters"></a>參數  
 `key`  
 指定用來查閱對應的字串。  
  
### <a name="return-value"></a>傳回值  
 非零，如果找到並成功移除，則此項目否則為 0。  
  
### <a name="remarks"></a>備註  
 如果，這可能會造成記憶體流失`CObject`物件不會刪除其他位置。  
  
 下表顯示的其他成員函式，類似於`CMapStringToOb::RemoveKey`。  
  
|類別|成員函式|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL RemoveKey (void\* ** `key` **);**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL RemoveKey (void\* ** `key` **);**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL RemoveKey (LPCTSTR** `key` **);**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL RemoveKey (LPCTSTR** `key` **);**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL RemoveKey (WORD** `key` **);**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL RemoveKey (WORD** `key` **);**|  
  
### <a name="example"></a>範例  
 請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)的清單`CAge`所有集合範例中使用的類別。  
  
 [!code-cpp[NVC_MFCCollections #&70;](../../mfc/codesnippet/cpp/cmapstringtoob-class_9.cpp)]  
  
 此程式的結果如下所示︰  
  
 `RemoveKey example: A CMapStringToOb with 3 elements`  
  
 `[Marge] = a CAge at $49A0 35`  
  
 `[Homer] = a CAge at $495E 36`  
  
 `[Bart] = a CAge at $4634 13`  
  
##  <a name="setat"></a>CMapStringToOb::SetAt  
 主要表示要插入對應中的項目。  
  
```  
void SetAt(
    LPCTSTR key,  
    CObject* newValue);
```  
  
### <a name="parameters"></a>參數  
 `key`  
 指定新項目的索引鍵的字串。  
  
 `newValue`  
 指定`CObject`是新的項目值的指標。  
  
### <a name="remarks"></a>備註  
 首先，索引鍵查閱。 如果找到索引鍵，則對應的值變更時。否則會建立新的索引鍵 / 值項目。  
  
 下表顯示的其他成員函式，類似於`CMapStringToOb::SetAt`。  
  
|類別|成員函式|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void SetAt( void\*** `key` **, void\*** `newValue` **);**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void SetAt( void\*** `key` **, WORD** `newValue` **);**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void SetAt( LPCTSTR** `key` **, void\*** `newValue` **);**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void SetAt( LPCTSTR** `key` **, LPCTSTR** `newValue` **);**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void SetAt( WORD** `key` **, CObject\*** `newValue` **);**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void SetAt( WORD** `key` **, void\*** `newValue` **);**|  
  
### <a name="example"></a>範例  
 請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)的清單`CAge`所有集合範例中使用的類別。  
  
 [!code-cpp[NVC_MFCCollections #&71;](../../mfc/codesnippet/cpp/cmapstringtoob-class_10.cpp)]  
  
 此程式的結果如下所示︰  
  
 `before Lisa's birthday: A CMapStringToOb with 2 elements`  
  
 `[Lisa] = a CAge at $493C 11`  
  
 `[Bart] = a CAge at $4654 13`  
  
 `after Lisa's birthday: A CMapStringToOb with 2 elements`  
  
 `[Lisa] = a CAge at $49C0 12`  
  
 `[Bart] = a CAge at $4654 13`  
  
## <a name="see-also"></a>另請參閱  
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CMapPtrToPtr 類別](../../mfc/reference/cmapptrtoptr-class.md)   
 [CMapPtrToWord 類別](../../mfc/reference/cmapptrtoword-class.md)   
 [CMapStringToPtr 類別](../../mfc/reference/cmapstringtoptr-class.md)   
 [CMapStringToString 類別](../../mfc/reference/cmapstringtostring-class.md)   
 [CMapWordToOb 類別](../../mfc/reference/cmapwordtoob-class.md)   
 [CMapWordToPtr 類別](../../mfc/reference/cmapwordtoptr-class.md)


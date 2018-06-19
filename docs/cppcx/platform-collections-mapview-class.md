---
title: Platform::Collections::MapView 類別 |Microsoft 文件
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::MapView::MapView
- COLLECTION/Platform::Collections::MapView::First
- COLLECTION/Platform::Collections::MapView::HasKey
- COLLECTION/Platform::Collections::MapView::Lookup
- COLLECTION/Platform::Collections::MapView::Size
- COLLECTION/Platform::Collections::MapView::Split
dev_langs:
- C++
helpviewer_keywords:
- MapView Class
ms.assetid: 9577dde7-f599-43c6-b1e4-7d653706fd62
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9b5000ad06e542aa4616a29150601b8d628fc097
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33091527"
---
# <a name="platformcollectionsmapview-class"></a>Platform::Collections::MapView 類別
表示 *對應 (Map)*(機碼值組的集合) 的唯讀檢視。  
  
## <a name="syntax"></a>語法  
  
```  
template <  
   typename K,  
   typename V,  
   typename C = ::std::less<K>>  
ref class MapView sealed;  
```  
  
#### <a name="parameters"></a>參數  
 `K`  
 機碼值組中，機碼的類型。  
  
 `V`  
 機碼值組中，值的型別。  
  
 `C`  
 一個類型，提供函式物件，可以根據排序鍵比較兩個項目值，以判斷它們在 MapView 中的相對順序。 根據預設， [std:: less<>\<K >](../standard-library/less-struct.md)。  
  
### <a name="remarks"></a>備註  
 MapView 是具象 c + + 實作[Windows::Foundation::Collections::IMapView \<K，V >](http://go.microsoft.com/fwlink/p/?LinkId=262409)應用程式二進位介面 (ABI) 之間傳遞的介面。 如需詳細資訊，請參閱 [集合 (C++/CX)](../cppcx/collections-c-cx.md)。  
  
### <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[Mapview:: Mapview](#ctor)|初始化 MapView 類別的新執行個體。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[Mapview:: First](#first)|傳回迭代器，初始化為對應檢視中的第一個元素。|  
|[Mapview:: Haskey](#haskey)|判斷目前 MapView 是否包含指定的機碼。|  
|[Mapview:: Lookup](#lookup)|在目前 MapView 物件中擷取位於指定機碼的元素。|  
|[Mapview:: Size](#size)|傳回目前 MapView 物件中的項目數。|  
|[MapView::Split](#split)|將原始 MapView 物件分割為兩個 MapView 物件。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `MapView`  
  
### <a name="requirements"></a>需求  
 **標頭：** collection.h  
  
 **命名空間：** Platform::Collections  


## <a name="first"></a> Mapview:: First 方法
傳回指定對應檢視中之第一個項目的迭代器。  
  
### <a name="syntax"></a>語法  
  
```    
virtual Windows::Foundation::Collections::IIterator<  
   Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();  
```  
  
### <a name="return-value"></a>傳回值  
 迭代器，指定對應檢視中的第一個元素。  
  
### <a name="remarks"></a>備註  
 若要保留 first （） 所傳回的迭代器的簡便方法是宣告的變數指派傳回值**自動**型别推斷關鍵字。 例如，`auto x = myMapView->First();`。  
  


## <a name="haskey"></a>  Mapview:: Haskey 方法
判斷目前 MapView 是否包含指定的機碼。  
  
### <a name="syntax"></a>語法  
  
```  
  
bool HasKey(K key);  
```  
  
### <a name="parameters"></a>參數  
 `key`  
 用來尋找 MapView 項目的機碼。 型別`key`為 typename *K*。  
  
### <a name="return-value"></a>傳回值  
 如果找到機碼則為 `true`，否則為 `false`。  
  


##  <a name="lookup"></a> Mapview:: Lookup 方法
取得與類型為 K 之指定機碼相關聯且類型為 V 的值。  
  
### <a name="syntax"></a>語法  
  
```  
V Lookup(K key);  
```  
  
### <a name="parameters"></a>參數  
 `key`  
 用來在 MapView 中尋找元素的機碼。 型別`key`為 typename *K*。  
  
### <a name="return-value"></a>傳回值  
 與 `key` 配對的值。 傳回值的類型為 typename *V*。  
  


##  <a name="ctor"></a> Mapview:: Mapview 建構函式
初始化 MapView 類別的新執行個體。  
  
### <a name="syntax"></a>語法  
  
```cpp  
explicit MapView(const C& comp = C());  
  
explicit MapView(const ::std::map<K, V, C>& m);  
  
explicit MapView(std::map<K, V, C>&& m);  
  
template <typename InIt> MapView(  
    InIt first,  
    InIt last,  
    const C& comp = C());  
  
MapView(
    ::std::initializer_list<std::pair<const K, V>> il,  
    const C& comp = C());  
```  
  
### <a name="parameters"></a>參數  
 `InIt`  
 目前 MapView 的 typename。  
  
 `comp`  
 函式物件。這個函式物件可以根據排序機碼比較兩個元素值，判斷它們在 MapView 中的相對順序。  
  
 `m`  
 參考或[Lvalues 和 Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)至`map Class`用來初始化目前 MapView。  
  
 `first`  
 用來初始化目前 MapView 的項目範圍中，第一個項目的輸入迭代器。  
  
 `last`  
 用來初始化目前 MapView 的項目範圍以外第一個項目的輸入迭代器。  
  
 il  
 A [std:: initializer_list < std:: pair\<K，V >>](../standard-library/initializer-list-class.md)其項目會插入至 MapView。  



##  <a name="size"></a> Mapview:: Size 方法
傳回目前 MapView 物件中的項目數。  
  
### <a name="syntax"></a>語法  
  
```cpp  
  
virtual property unsigned int Size;  
```  
  
### <a name="return-value"></a>傳回值  
 目前 MapView 中的項目數。  
  


##  <a name="split"></a> Mapview:: Split 方法
將目前 MapView 物件分割為兩個 MapView 物件。 這個方法無法操作。  
  
### <a name="syntax"></a>語法  
  
```  
void Split(  
   Windows::Foundation::Collections::IMapView<  
                         K, V>^ * firstPartition,  
   Windows::Foundation::Collections::IMapView<  
                         K, V>^ * secondPartition);  
```  
  
### <a name="parameters"></a>參數  
 `firstPartition`  
 原始 MapView 物件的第一個部分。  
  
 `secondPartition`  
 原始 MapView 物件的第二個部分。  
  
### <a name="remarks"></a>備註  
 這個方法無法操作，不會執行任何動作。  
    
## <a name="see-also"></a>另請參閱  
 [Platform 命名空間](platform-namespace-c-cx.md)
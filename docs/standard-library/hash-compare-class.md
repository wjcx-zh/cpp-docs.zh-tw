---
title: hash_compare 類別
ms.date: 11/04/2016
f1_keywords:
- hash_set/stdext::hash_compare
helpviewer_keywords:
- hash_compare class
ms.assetid: d502bb59-de57-4585-beb9-00e3a998c0af
ms.openlocfilehash: 4fb44a371630a66275f6ef59a0bf66b4cb73a71f
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689553"
---
# <a name="hash_compare-class"></a>hash_compare 類別

類別樣板描述可供任何雜湊關聯容器（hash_map、hash_multimap、hash_set 或 hash_multiset）使用的物件，做為預設的**特性**參數物件，以排序及雜湊其包含的元素。

## <a name="syntax"></a>語法

class hash_compare { Traits comp; public: const size_t bucket_size = 4; const size_t min_buckets = 8; hash_compare(); hash_compare(Traits pred); size_t operator()(const Key& key) const; bool operator()( const Key& key1, const Key& key2) const; };

## <a name="remarks"></a>備註

每個雜湊關聯容器都會儲存類型 `Traits` （範本參數）的雜湊特性物件。 您可以選擇性地覆寫特定函式與物件，從特製的 hash_compare 衍生類別，或如果您符合特定的基本需求，則可以提供您自己這個類別的版本。 具體而言，針對 `hash_compare<Key, Traits>` 類型的物件 hash_comp，上述的容器需要下列行為：

- 對於 `Key` 類型 `key` 的所有值，呼叫**hash_comp**（`key`）會當做雜湊函式，此函式會產生 `size_t` 類型值的分佈。 hash_compare 所提供的函式會傳回 `key`。

- 針對在序列中 `key2` 之前 `Key` 的任何值 `key1`，並具有相同的雜湊值（雜湊函式所傳回的值）， **hash_comp**（`key2`，`key1`）為 false。 函數必須對 `Key` 類型的值加總排序。 Hash_compare 所提供的函式會傳回*comp*（`key2`，`key1`） `,` 其中， *comp*是類型 `Traits` 的預存物件，您可以在建立 hash_comp 物件時加以指定。 針對預設 `Traits` 參數類型 `less<Key>`，排序索引鍵永遠不會減少值。

- 整數常數 `bucket_size` 指定每個「值區」（雜湊表專案）的平均元素數，容器應該不會嘗試超過此數目。 此數目必須大於零。 hash_compare 所提供的值為 4。

- 整數常數 `min_buckets` 指定要在雜湊表中維持的最小值區數目。 此數目必須是二次方且大於零。 hash_compare 所提供的值為 8。

## <a name="example"></a>範例

如需如何宣告及使用 hash_compare 的範例，請參閱 [hash_map::hash_map](../standard-library/hash-map-class.md#hash_map)、[hash_multimap::hash_multimap](../standard-library/hash-multimap-class.md#hash_multimap)、[hash_set::hash_set](../standard-library/hash-set-class.md#hash_set) 及 [hash_multiset::hash_multiset](../standard-library/hash-multiset-class.md#hash_multiset) 的範例。

## <a name="requirements"></a>需求

**標頭：** \<hash_map>

**命名空間：** stdext

## <a name="see-also"></a>請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)

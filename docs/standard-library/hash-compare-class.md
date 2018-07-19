---
title: hash_compare 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- hash_set/stdext::hash_compare
dev_langs:
- C++
helpviewer_keywords:
- hash_compare class
ms.assetid: d502bb59-de57-4585-beb9-00e3a998c0af
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 92dce97754eccc8cd4f618db3ac3e23574fb54ae
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38956570"
---
# <a name="hashcompare-class"></a>hash_compare 類別

此範本類別描述的物件可供任一雜湊關聯容器 (hash_map、hash_multimap、hash_set 或 hash_multiset) 作為預設 **Traits** 參數物件，用來排序及雜湊處理它們所包含的元素。

## <a name="syntax"></a>語法

class hash_compare { Traits comp; public: const size_t bucket_size = 4; const size_t min_buckets = 8; hash_compare(); hash_compare(Traits pred); size_t operator()(const Key& key) const; bool operator()( const Key& key1, const Key& key2) const; };

## <a name="remarks"></a>備註

每個雜湊關聯容器都會儲存類型的雜湊特性物件`Traits`（範本參數）。 您可以選擇性地覆寫特定函式與物件，從特製的 hash_compare 衍生類別，或如果您符合特定的基本需求，則可以提供您自己這個類別的版本。 尤其是針對類型的 hash_comp 物件`hash_compare<Key, Traits>`，上述容器需要下列行為：

- 所有值`key`型別的`Key`，在呼叫**hash_comp**(`key`) 做為雜湊函式，會產生類型的值分佈`size_t`。 hash_compare 所提供的函式會傳回 `key`。

- 每個值`key1`型別的`Key`前面`key2`序列中且具有相同雜湊值 （值的雜湊函式所傳回）， **hash_comp**(`key2`， `key1`) 為 false。 函式必須加上總排序類型的值`Key`。 Hash_compare 所提供的函式會傳回*comp*(`key2`， `key1`)`,`其中*comp*是類型的預存的物件`Traits`，您可以指定當您建構 hash_comp 物件。 預設值`Traits`參數類型`less<Key>`，永遠不會減少值中的排序索引鍵。

- 整數常數`bucket_size`指定項目，每個 「 值區 」 （雜湊資料表項目） 的容器應該不能超過的平均數目。 此數目必須大於零。 hash_compare 所提供的值為 4。

- 整數常數`min_buckets`指定貯體，以維護雜湊表中的最小數目。 此數目必須是二次方且大於零。 hash_compare 所提供的值為 8。

## <a name="example"></a>範例

如需如何宣告及使用 hash_compare 的範例，請參閱 [hash_map::hash_map](../standard-library/hash-map-class.md#hash_map)、[hash_multimap::hash_multimap](../standard-library/hash-multimap-class.md#hash_multimap)、[hash_set::hash_set](../standard-library/hash-set-class.md#hash_set) 及 [hash_multiset::hash_multiset](../standard-library/hash-multiset-class.md#hash_multiset) 的範例。

## <a name="requirements"></a>需求

**標頭：**\<hash_map>

**命名空間：** stdext

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)<br/>

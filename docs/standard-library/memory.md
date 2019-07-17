---
title: '&lt;memory&gt;'
ms.date: 04/04/2019
f1_keywords:
- memory/std::<memory>
- <memory>
- std::<memory>
helpviewer_keywords:
- memory header
ms.openlocfilehash: d2776e658b511208d9a295cd84a961d7691d29e0
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246814"
---
# <a name="ltmemorygt"></a>&lt;memory&gt;

定義幫助配置和釋放物件的類別、運算子和數個範本。

## <a name="requirements"></a>需求

**標頭：** \<memory>

**命名空間：** std

## <a name="members"></a>成員

### <a name="functions"></a>函式

|||
|-|-|
|[addressof](../standard-library/memory-functions.md#addressof)|取得物件真正的位址。|
|[align](../standard-library/memory-functions.md#align)|根據所提供的對齊和開始位址，傳回指向指定大小之範圍的指標。|
|[allocate_shared](../standard-library/memory-functions.md#allocate_shared)|建立 `shared_ptr`，指向透過指定的配置器為特定類型配置及建構的物件。|
|[atomic_compare_exchange_strong](../standard-library/memory-functions.md#atomic_compare_exchange_strong)||
|[atomic_compare_exchange_weak](../standard-library/memory-functions.md#atomic_compare_exchange_weak)||
|[atomic_compare_exchange_strong_explicit](../standard-library/memory-functions.md#atomic_compare_exchange_strong_explicit)||
|[atomic_compare_exchange_weak_explicit](../standard-library/memory-functions.md#atomic_compare_exchange_weak_explicit)||
|[atomic_exchange](../standard-library/memory-functions.md#atomic_exchange)||
|[atomic_exchange_explicit](../standard-library/memory-functions.md#atomic_exchange_explicit)||
|[atomic_is_lock_free](../standard-library/memory-functions.md#atomic_is_lock_free)||
|[atomic_load](../standard-library/memory-functions.md#atomic_load)||
|[atomic_load_explicit](../standard-library/memory-functions.md#atomic_load_explicit)||
|[atomic_store](../standard-library/memory-functions.md#atomic_store)||
|[atomic_store_explicit](../standard-library/memory-functions.md#atomic_store_explicit)||
|[const_pointer_cast](../standard-library/memory-functions.md#const_pointer_cast)|常數轉型成 `shared_ptr`。|
|[declare_no_pointers](../standard-library/memory-functions.md#declare_no_pointers)|通知記憶體回收行程，在指定之位址開頭且落在指示之區塊大小內的字元不包含任何可追蹤指標。|
|[declare_reachable](../standard-library/memory-functions.md#declare_reachable)|告知記憶體回收，指示的位址是前往配置儲存體且可連接。|
|[default_delete](../standard-library/memory-functions.md#default_delete)|刪除使用 `operator new` 配置的物件。 適合搭配 `unique_ptr` 使用。|
|[destroy_at](../standard-library/memory-functions.md#destroy_at)|速記`destroy`方法。|
|[destroy](../standard-library/memory-functions.md#destroy)|速記`destroy`方法。|
|[destroy_n](../standard-library/memory-functions.md#destroy_n)|速記`destroy`方法。|
|[dynamic_pointer_cast](../standard-library/memory-functions.md#dynamic_pointer_cast)|動態轉型為 `shared_ptr`。|
|[get_deleter](../standard-library/memory-functions.md#get_deleter)|從 `shared_ptr` 取得刪除者。|
|[get_pointer_safety](../standard-library/memory-functions.md#get_pointer_safety)|傳回任何記憶體回收行程所假設之指標安全的類型。|
|[get_temporary_buffer](../standard-library/memory-functions.md#get_temporary_buffer)|為項目序列 (不超過指定的項目數目) 配置暫時儲存區。|
|[make_shared](../standard-library/memory-functions.md#make_shared)|建立並傳回 `shared_ptr`，它會指向使用預設配置器從零個或多個引數建構的配置物件。|
|[make_unique](../standard-library/memory-functions.md#make_unique)|建立並傳回 [unique_ptr](../standard-library/unique-ptr-class.md)0，它會指向從零個或多個引數建構的配置物件。|
|[pointer_safety](../standard-library/memory-enums.md#pointer_safety)|`get_pointer_safety` 所有可能的傳回值的列舉。|
|[return_temporary_buffer](../standard-library/memory-functions.md#return_temporary_buffer)|將使用 `get_temporary_buffer` 樣板函式配置的暫存記憶體取消配置。|
|[static_pointer_cast](../standard-library/memory-functions.md#static_pointer_cast)|靜態轉型至 `shared_ptr`。|
|[swap](../standard-library/memory-functions.md#swap)|交換兩個 `shared_ptr` 或 `weak_ptr` 物件。|
|[undeclare_no_pointers](../standard-library/memory-functions.md#undeclare_no_pointers)|通知記憶體回收行程，基底位址指標和區塊大小定義的記憶體區塊中的字元現在可能會包含可追蹤的指標。|
|[undeclare_reachable](../standard-library/memory-functions.md#undeclare_reachable)|通知 `garbage_collector`，指定的記憶體位置無法連接。|
|[uninitialized_copy](../standard-library/memory-functions.md#uninitialized_copy)|從指定的輸入範圍將物件複製到未初始化的目的範圍內。|
|[uninitialized_copy_n](../standard-library/memory-functions.md#uninitialized_copy_n)|從輸入迭代器建立所指定項目數的複本。 複本會放在正向迭代器中。|
|[uninitialized_default_construct](../standard-library/memory-functions.md#uninitialized_default_construct)|速記`uninitialized_default_construct`方法。|
|[uninitialized_default_construct_n](../standard-library/memory-functions.md#uninitialized_default_construct_n)|速記`uninitialized_construct`方法。|
|[uninitialized_fill](../standard-library/memory-functions.md#uninitialized_fill)|將所指定值的物件複製到未初始化的目的範圍內。|
|[uninitialized_fill_n](../standard-library/memory-functions.md#uninitialized_fill_n)|將所指定值的物件複製到未初始化目的範圍的指定項目數內。|
|[uninitialized_move](../standard-library/memory-functions.md#uninitialized_move)|速記`uninitialized_move`方法。|
|[uninitialized_move_n](../standard-library/memory-functions.md#uninitialized_move_n)|速記`uninitialized_move`方法。|
|[uninitialized_value_construct](../standard-library/memory-functions.md#uninitialized_value_construct)|速記`uninitialized_value_construct`方法。|
|[uninitialized_value_construct_n](../standard-library/memory-functions.md#uninitialized_value_construct_n)|速記`uninitialized_value_construct`方法。|
|[uses_allocator_v](../standard-library/memory-functions.md#uses_allocator_v)||

### <a name="operators"></a>運算子

|||
|-|-|
|[operator!=](../standard-library/memory-operators.md#op_neq)|測試指定類別的配置器物件之間是否不等。|
|[operator==](../standard-library/memory-operators.md#op_eq_eq)|測試指定類別的配置器物件之間是否相等。|
|[operator>=](../standard-library/memory-operators.md#op_gt_eq)|測試指定之類別的一個配置器物件是否大於或等於第二個配置器物件。|
|[operator<](../standard-library/memory-operators.md#op_lt)|測試指定之類別的一個物件是否小於第二個物件。|
|[operator\<=](../standard-library/memory-operators.md#op_gt_eq)|測試指定之類別的一個物件是否小於或等於第二個物件。|
|[operator>](../standard-library/memory-operators.md#op_gt)|測試指定之類別的一個物件是否大於第二個物件。|
|[operator<<](../standard-library/memory-operators.md#op_lt_lt)|`shared_ptr` 插入者。|

### <a name="classes"></a>類別

|||
|-|-|
|[allocator](../standard-library/allocator-class.md)|此範本類別描述一個物件，該物件會管理 **Type** 類型之物件陣列的儲存體配置和釋出。|
|[allocator_traits](../standard-library/allocator-traits-class.md)|描述物件，用來判斷啟用配置器之容器所需的所有資訊。|
|[auto_ptr](../standard-library/auto-ptr-class.md)|此範本類別描述可儲存類型的配置物件的指標**型別** <strong>\*</strong>這可確保它點被刪除時取得其上層 auto_ptr 物件損毀。|
|[bad_weak_ptr](../standard-library/bad-weak-ptr-class.md)|報告錯誤 weak_ptr 例外狀況。|
|[enabled_shared_from_this](../standard-library/enable-shared-from-this-class.md)|幫助產生 `shared_ptr`。|
|[pointer_traits](../standard-library/pointer-traits-struct.md)|提供樣板類別 `allocator_traits` 的物件所需的資訊，以描述具有指標類型 `Ptr` 的配置器。|
|[raw_storage_iterator](../standard-library/raw-storage-iterator-class.md)|提供的配接器類別，可讓演算法將其結果儲存至未初始化的記憶體。|
|[shared_ptr](../standard-library/shared-ptr-class.md)|將參考計數的智慧型指標環繞動態配置物件。|
|[unique_ptr](../standard-library/unique-ptr-class.md)|儲存自有物件的指標。 沒有任何其他 `unique_ptr` 擁有此指標。 終結擁有者時，也會終結 `unique_ptr`。|
|[weak_ptr](../standard-library/weak-ptr-class.md)|包裝弱式連結的指標。|

### <a name="structures"></a>結構

|||
|-|-|
|[allocator_arg_t](../standard-library/allocator-class.md#allocator_arg_t)||
|[default_delete](../standard-library/default-delete-struct.md)||
|[hash]()||
|[owner_less](../standard-library/memory-functions.md#owner_less)|允許按擁有權混合比較共用指標和弱式指標。|
|[uses_allocator](../standard-library/allocator-class.md#uses_allocator)||

### <a name="specializations"></a>特製化

|||
|-|-|
|[allocator\<void>](../standard-library/allocator-void-class.md)|void 類型的樣板類別配置器特製化，只用於定義在此特殊內容中具有意義的成員形別。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>

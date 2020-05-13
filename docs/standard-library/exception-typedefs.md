---
title: '&lt;exception&gt; typedefs'
ms.date: 11/04/2016
f1_keywords:
- exception/std::exception_ptr
- exception/std::terminate_handler
- exception/std::unexpected_handler
ms.assetid: 2a338480-35e2-46f7-b223-52d4e84a5768
ms.openlocfilehash: f71c03e0c0a2e7ea4f37a85e85628ccf630ea317
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368729"
---
# <a name="ltexceptiongt-typedefs"></a>&lt;exception&gt; typedefs

## <a name="exception_ptr"></a><a name="exception_ptr"></a>exception_ptr

描述例外狀況指標的類型。

```cpp
typedef unspecified exception_ptr;
```

### <a name="remarks"></a>備註

用於實作 `exception_ptr` 類型的未指定內部類別。

利用 `exception_ptr` 物件參考目前的例外狀況或使用者指定的例外狀況執行個體。 在 Microsoft 實作中，例外狀況是以 [EXCEPTION_RECORD](/windows/win32/api/winnt/ns-winnt-exception_record) 結構表示。 每個 `exception_ptr` 物件均包含一個例外狀況參考欄位，指向代表該例外狀況的 `EXCEPTION_RECORD` 結構複本。

當您宣告 `exception_ptr` 變數時，此變數尚未關聯任何例外狀況。 也就是說，其例外狀況參考欄位為 NULL。 這樣的 `exception_ptr` 物件稱為 *null exception_ptr*。

利用 `current_exception` 或 `make_exception_ptr` 函式將例外狀況指派給 `exception_ptr` 物件。 當您將例外狀況指派給 `exception_ptr` 變數時，此變數的例外狀況參考欄位會指向該例外狀況的複本。 如果記憶體空間不足，無法複製該例外狀況，則例外狀況參考欄位會指向 [std::bad_alloc](../standard-library/bad-alloc-class.md) 例外狀況的複本。 如果`current_exception`或`make_exception_ptr`函數由於任何其他原因無法複製異常,則函數調用`terminate`CRT函數以退出當前進程。

`exception_ptr` 物件本身並不是指標 (儘管其名稱如此)。 此物件不會遵守指標語意，也不能搭配指標成員存取 (`->`) 或間接取值 (*) 運算子使用。 `exception_ptr` 物件沒有公用資料成員或成員函式。

**比較:**

您可以使用等於 (`==`) 和不等於 (`!=`) 運算子比較兩個 `exception_ptr` 物件。 運算子不會比較代表例外狀況之 `EXCEPTION_RECORD` 結構的二進位值 (位元模式)。 相反地，運算子會比較 `exception_ptr` 物件的例外狀況參考欄位位址。 因此，Null `exception_ptr` 和 Null 值的比較結果是相等。

## <a name="terminate_handler"></a><a name="terminate_handler"></a>terminate_handler

此類型描述適合做為 `terminate_handler` 之函式的指標。

```cpp
typedef void (*terminate_handler)();
```

### <a name="remarks"></a>備註

此類型描述適合做為終止處理常式之函式的指標。

### <a name="example"></a>範例

如需 `terminate_handler` 的用法範例，請參閱 [set_terminate](../standard-library/exception-functions.md#set_terminate)。

## <a name="unexpected_handler"></a><a name="unexpected_handler"></a>unexpected_handler

此類型描述的函式指標適合作為 `unexpected_handler`。

```cpp
typedef void (*unexpected_handler)();
```

### <a name="example"></a>範例

如需 `unexpected_handler` 的用法範例，請參閱 [set_unexpected](../standard-library/exception-functions.md#set_unexpected)。

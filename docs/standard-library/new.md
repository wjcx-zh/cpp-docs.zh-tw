---
title: '&lt;new&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <new>
dev_langs:
- C++
helpviewer_keywords:
- new header
ms.assetid: 218e2a15-34e8-4ef3-9122-1e90eccf8559
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 03d4019f86f99c73ccb25c5cf570637dbf0d7753
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38966497"
---
# <a name="ltnewgt"></a>&lt;new&gt;

定義數個類型和函式，對在程式控制下之儲存體控制配置和釋放。 它也會定義儲存體管理錯誤報告的元件。

## <a name="syntax"></a>語法

```cpp
#include <new>

```

## <a name="remarks"></a>備註

在這個標頭宣告的某些函式為可取代的。 此實作提供預設版本，會在本文件中描述其行為。 然而程式可能以相同簽章定義函式，藉此在連結時取代預設版本。 此取代版本必須符合本文件中描述的需求。

### <a name="objects"></a>物件

|||
|-|-|
|[nothrow](../standard-library/new-functions.md#nothrow)|提供要用來做為引數物件**nothrow**新版**新**並**刪除**。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[new_handler](../standard-library/new-typedefs.md#new_handler)|類型，指向適合做為新的處理常式使用之函式。|

### <a name="functions"></a>函式

|功能|描述|
|-|-|
|[set_new_handler](../standard-library/new-functions.md#set_new_handler)|當嘗試配置記憶體發生新的錯誤時，安裝此時所呼叫的使用者函式。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator delete](../standard-library/new-operators.md#op_delete)|由 delete 陳述式呼叫的函式，藉此取消配置物件個體的儲存區。|
|[operator delete&#91;&#93;](../standard-library/new-operators.md#op_delete_arr)|由 delete 陳述式呼叫的函式，藉此取消配置物件陣列的儲存區。|
|[operator new](../standard-library/new-operators.md#op_new)|由 new 陳述式呼叫的函式，藉此配置物件個體的儲存區。|
|[operator new&#91;&#93;](../standard-library/new-operators.md#op_new_arr)|由 new 陳述式呼叫的函式，藉此配置物件陣列的儲存區。|

### <a name="classes"></a>類別

|類別|描述|
|-|-|
|[bad_alloc 類別](../standard-library/bad-alloc-class.md)|描述擲回例外狀況的類別，該例外狀況表示配置要求失敗。|
|[nothrow_t 類別](../standard-library/nothrow-t-structure.md)|該類別可做為 new 運算子的函式參數使用，藉此表示此函式應該要傳回 null 指標，報告配置失敗，而非擲回例外狀況。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>

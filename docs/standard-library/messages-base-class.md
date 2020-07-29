---
title: messages_base 類別
ms.date: 11/04/2016
f1_keywords:
- xlocmes/std::messages_base
helpviewer_keywords:
- messages_base class
ms.assetid: 9aad38c6-4c13-445d-b096-364bd0836efb
ms.openlocfilehash: b0fe7d66842fb77c6fd03f62b012babcbc9f7f3a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215643"
---
# <a name="messages_base-class"></a>messages_base 類別

基類描述 **`int`** 訊息目錄的類型。

## <a name="syntax"></a>語法

```cpp
struct messages_base : locale::facet {
    typedef int catalog;
    explicit messages_base(size_t _Refs = 0)
};
```

## <a name="remarks"></a>備註

類型目錄是類型 **`int`** 的同義字，描述來自訊息的可能傳回值：： [do_open](../standard-library/messages-class.md#do_open)。

## <a name="requirements"></a>需求

**標頭：**\<locale>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

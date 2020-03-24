---
title: uuid (C++)
ms.date: 11/04/2016
f1_keywords:
- uuid_cpp
helpviewer_keywords:
- __declspec keyword [C++], uuid
- uuid __declspec keyword
ms.assetid: 9d004621-09bc-4a8d-871b-648f5d5102d7
ms.openlocfilehash: 09e40d38382bea0f902fda03d15d24e0cf1a627d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187800"
---
# <a name="uuid-c"></a>uuid (C++)

**Microsoft 專屬**

編譯器會使用**uuid**屬性，將 GUID 附加至宣告或定義的類別或結構（僅限完整的 COM 物件定義）。

## <a name="syntax"></a>語法

```
__declspec( uuid("ComObjectGUID") ) declarator
```

## <a name="remarks"></a>備註

**Uuid**屬性會接受字串做為其引數。 這個字串會以一般登錄格式來命名 GUID，其中包含或不含 **{}** 分隔符號。 例如：

```cpp
struct __declspec(uuid("00000000-0000-0000-c000-000000000046")) IUnknown;
struct __declspec(uuid("{00020400-0000-0000-c000-000000000046}")) IDispatch;
```

這個屬性可以在重新宣告中套用。 這可讓系統標頭提供介面的定義（例如 `IUnknown`）以及其他標頭中的重新宣告（例如 \<comdef.h >），以提供 GUID。

關鍵字[__uuidof](../cpp/uuidof-operator.md)可以套用來抓取附加至使用者自訂類型的常數 GUID。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[__declspec](../cpp/declspec.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)

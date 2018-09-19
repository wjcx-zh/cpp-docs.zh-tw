---
title: uuid （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- uuid_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], uuid
- uuid __declspec keyword
ms.assetid: 9d004621-09bc-4a8d-871b-648f5d5102d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 44799b507fb9c27cb1d9f166e86228ed6003a0d8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086183"
---
# <a name="uuid-c"></a>uuid (C++)

**Microsoft 專屬**

編譯器會將 GUID 附加至類別或結構宣告或定義 （完整 COM 物件定義只有） 使用**uuid**屬性。

## <a name="syntax"></a>語法

```
__declspec( uuid("ComObjectGUID") ) declarator
```

## <a name="remarks"></a>備註

**Uuid**屬性會採用字串作為其引數。 此字串名稱的 GUID，以標準登錄格式包含或不含 **{}** 分隔符號。 例如: 

```cpp
struct __declspec(uuid("00000000-0000-0000-c000-000000000046")) IUnknown;
struct __declspec(uuid("{00020400-0000-0000-c000-000000000046}")) IDispatch;
```

這個屬性可以在重新宣告中套用。 這可讓系統標頭提供介面的定義，例如`IUnknown`，並在某些其他標頭中的重新宣告 (例如\<comdef.h >) 以提供 GUID。

關鍵字[__uuidof](../cpp/uuidof-operator.md)可以套用至擷取 GUID 附加至使用者定義類型的常數。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[__declspec](../cpp/declspec.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)
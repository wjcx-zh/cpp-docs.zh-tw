---
title: raw_dispinterfaces
ms.date: 11/04/2016
f1_keywords:
- raw_dispinterfaces
helpviewer_keywords:
- raw_dispinterfaces attribute
ms.assetid: f762864d-29bf-445b-825a-ba7b29a95409
ms.openlocfilehash: 8a6c335c7afe2cc56613f06abf5c181f05f6bfec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50585389"
---
# <a name="rawdispinterfaces"></a>raw_dispinterfaces
**C + + 特定**

告知編譯器来產生低階包裝函式的呼叫 dispinterface 方法和屬性`IDispatch::Invoke`並傳回的 HRESULT 錯誤碼。

## <a name="syntax"></a>語法

```
raw_dispinterfaces
```

## <a name="remarks"></a>備註

如果沒有指定此屬性，只會產生高階包裝函式，一旦失敗就會擲回 C++ 例外狀況。

**END c + + 特定的**

## <a name="see-also"></a>另請參閱

[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)
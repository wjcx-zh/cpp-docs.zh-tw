---
title: raw_dispinterfaces
ms.date: 11/04/2016
f1_keywords:
- raw_dispinterfaces
helpviewer_keywords:
- raw_dispinterfaces attribute
ms.assetid: f762864d-29bf-445b-825a-ba7b29a95409
ms.openlocfilehash: ef8ed3992c77df0f1d551e923ddc90c2d1bb9b0b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62179837"
---
# <a name="rawdispinterfaces"></a>raw_dispinterfaces
**C++特定**

告知編譯器来產生低階包裝函式的呼叫 dispinterface 方法和屬性`IDispatch::Invoke`並傳回的 HRESULT 錯誤碼。

## <a name="syntax"></a>語法

```
raw_dispinterfaces
```

## <a name="remarks"></a>備註

如果沒有指定此屬性，只會產生高階包裝函式，一旦失敗就會擲回 C++ 例外狀況。

**結束C++特定**

## <a name="see-also"></a>另請參閱

[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)
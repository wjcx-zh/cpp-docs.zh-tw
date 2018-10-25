---
title: raw_dispinterfaces |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- raw_dispinterfaces
dev_langs:
- C++
helpviewer_keywords:
- raw_dispinterfaces attribute
ms.assetid: f762864d-29bf-445b-825a-ba7b29a95409
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b89c1f549168a762b5ae095c4eacf5ddb1b4d053
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50062344"
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
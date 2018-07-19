---
title: vector&lt;bool&gt;::reference 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- vector/vector<bool>::reference
dev_langs:
- C++
helpviewer_keywords:
- vector<bool> reference class
ms.assetid: f27854f9-0ef0-4e7e-ad2e-cd53b6cb3334
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c87975e0b27934d091e896867620011a51b78d52
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38966520"
---
# <a name="vectorltboolgtreference-class"></a>vector&lt;bool&gt;::reference 類別

`vector<bool>::reference` 類別是 [vector\<bool> 類別](../standard-library/vector-bool-class.md)提供的 Proxy 類別，用來模擬 `bool&`。

## <a name="remarks"></a>備註

需要模擬參考，因為 C++ 原生不允許對位元的直接參考。 `vector<bool>` 對每個項目只使用一個位元，您可以使用這個 Proxy 類別來參考位元。 不過，因為某些指派無效，參考模擬不完整。 例如，因為 `vector<bool>::reference` 物件位址無法採用，使用 [vector\<bool>::operator&#91;&#93;](http://msdn.microsoft.com/Library/97738633-690d-4069-b2d9-8c54104fbfdd) 的下列程式碼不正確：

```cpp
vector<bool> vb;
// ...
bool* pb = &vb[1]; // conversion error - do not use
bool& refb = vb[1];   // conversion error - do not use
```

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[flip](../standard-library/vector-bool-reference-flip.md)|反轉向量項目的布林值。|
|[operator bool](../standard-library/vector-bool-reference-operator-bool.md)|提供的隱含轉換`vector<bool>::reference`要**bool**。|
|[operator=](../standard-library/vector-bool-reference-operator-assign.md)|將布林值指派給位元，或是將參考的項目所表示的值指派給位元。|

## <a name="requirements"></a>需求

**標頭**：\<vector>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[\<vector>](../standard-library/vector.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)<br/>

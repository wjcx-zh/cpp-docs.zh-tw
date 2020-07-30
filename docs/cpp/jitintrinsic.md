---
title: jitintrinsic
ms.date: 11/04/2016
f1_keywords:
- jitintrinsic
- jitintrinsic_cpp
helpviewer_keywords:
- __declspec keyword [C++], jitintrinsic
- jitintrinsic __declspec modifier
ms.assetid: 23dbe416-7ef6-442b-b16d-9a81aab04fa6
ms.openlocfilehash: cecadcad15ee65a44ad5a8245efdb69903c89459
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233700"
---
# <a name="jitintrinsic"></a>jitintrinsic

將函式標記為 64 位元 Common Language Runtime 的必要項。 這種方式會在 Microsoft 所提供程式庫中的某些函式上使用。

## <a name="syntax"></a>語法

```
__declspec(jitintrinsic)
```

## <a name="remarks"></a>備註

**`jitintrinsic`** 將 MODOPT （）加入至函式簽章 <xref:System.Runtime.CompilerServices.IsJitIntrinsic> 。

不鼓勵使用者使用此 **`__declspec`** 修飾詞，因為可能會發生非預期的結果。

## <a name="see-also"></a>另請參閱

[__declspec](../cpp/declspec.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)

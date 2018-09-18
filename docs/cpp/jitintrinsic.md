---
title: jitintrinsic |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- jitintrinsic
- jitintrinsic_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], jitintrinsic
- jitintrinsic __declspec modifier
ms.assetid: 23dbe416-7ef6-442b-b16d-9a81aab04fa6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 888ec19eaedf881fed97a14a7f3f8b5ee673ce7a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056283"
---
# <a name="jitintrinsic"></a>jitintrinsic

將函式標記為 64 位元 Common Language Runtime 的必要項。 這種方式會在 Microsoft 所提供程式庫中的某些函式上使用。

## <a name="syntax"></a>語法

```
__declspec(jitintrinsic)
```

## <a name="remarks"></a>備註

**jitintrinsic**將 MODOPT (<xref:System.Runtime.CompilerServices.IsJitIntrinsic>) 至函式簽章。

不建議使用此使用者 **__declspec**修飾詞為非預期的結果可能會發生。

## <a name="see-also"></a>另請參閱

[__declspec](../cpp/declspec.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)
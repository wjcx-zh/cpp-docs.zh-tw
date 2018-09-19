---
title: 編譯器錯誤 C3462 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3462
dev_langs:
- C++
helpviewer_keywords:
- C3462
ms.assetid: 56b75f35-9fad-42d9-a969-eeca5d709bec
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eba9e063b60ff60403b8b4cc7136ccd1313ecc47
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028034"
---
# <a name="compiler-error-c3462"></a>編譯器錯誤 C3462

'type': 只能轉送匯入的類型

TypeForwardedTo 屬性必須套用至參考的中繼資料中的類型。

如需詳細資訊，請參閱 <<c0> [ 型別轉送 (C + + /cli CLI)](../../windows/type-forwarding-cpp-cli.md)。

## <a name="example"></a>範例

下列範例會建立元件。

```
// C3462.cpp
// compile with: /clr /LD
public ref class R {};
```

## <a name="example"></a>範例

下列範例會產生 C3462：

```
// C3462b.cpp
// compile with: /clr /c
#using "C3462.dll"
ref class N {};
[assembly:TypeForwardedTo(N::typeid)];   // C3462
[assembly:TypeForwardedTo(R::typeid)];
```
---
title: 編譯器警告 （層級 1） C4691 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4691
dev_langs:
- C++
helpviewer_keywords:
- C4691
ms.assetid: 722133d9-87f6-46c1-9e86-9825453d6999
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ca063d61b799a10bd1d629fdba1293e0a66b0752
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46095114"
---
# <a name="compiler-warning-level-1-c4691"></a>編譯器警告 (層級 1) C4691

'type': 未參考組件 'file'，改用目前的轉譯單位中定義的型別中，必須參考型別

未參考包含原始型別定義的中繼資料檔案，且編譯器使用本機的型別定義。

在您重建的情況下*檔案*，可以忽略 C4691，或使用 pragma 關閉[警告](../../preprocessor/warning.md)。  也就是說，如果您要建置的檔案是編譯器會找不到型別定義預期的檔案同名，您可以忽略 C4691。

不過，如果編譯器會使用不是來自相同的組件中繼資料; 中所參考的定義可能會發生未預期的行為不只是可以類型的名稱，還可以將組件的 CLR 型別是型別。  也就是來自組件 z.dll 的型別 Z 是不同於從組件 y.dll 類型 Z。

## <a name="example"></a>範例

此範例包含原始型別定義。

```
// C4691_a.cpp
// compile with: /clr /LD /W1
public ref class Original_Type {};
```

## <a name="example"></a>範例

此範例會參考 C4691_a.dll 和宣告類型 Original_Type 的欄位。

```
// C4691_b.cpp
// compile with: /clr /LD
#using "C4691_a.dll"
public ref class Client {
public:
   Original_Type^ ot;
};
```

## <a name="example"></a>範例

下列範例會產生 C4691。  請注意此範例包含 Original_Type xml 定義，且未參考 C4691a.dll。

若要解決，參考包含原始型別定義的中繼資料檔案，並移除區域宣告和定義。

```
// C4691_c.cpp
// compile with: /clr /LD /W1
// C4691 expected

// Uncomment the following line to resolve.
// #using "C4691_a.dll"
#using "C4691_b.dll"

// Delete the following line to resolve.
ref class Original_Type;

public ref class MyClass : Client {};
```
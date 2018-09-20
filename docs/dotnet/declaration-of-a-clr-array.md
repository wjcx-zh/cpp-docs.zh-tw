---
title: CLR 陣列的宣告 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- array keyword [C++]
ms.assetid: 36a8883c-2663-43f0-a90c-28f27035e036
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c3de17bb293e10c4e1a2287ef12b934633b1fe21
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426454"
---
# <a name="declaration-of-a-clr-array"></a>CLR 陣列的宣告

宣告的語法，具現化，並初始化 managed 的陣列已從 Managed Extensions for c + + Visual c + +。

Managed Extensions 中的 CLR 陣列物件的宣告是標準陣列宣告中的延伸模組`__gc`陣列物件的名稱和其可能是逗號填入維度，如同下列配對之間放置關鍵字範例：

```
void PrintValues( Object* myArr __gc[]);
void PrintValues( int myArr __gc[,,]);
```

這已簡化在新的語法中，我們可以在其中使用類似於 c + + 標準程式庫的範本型宣告`vector`宣告。 第一個參數表示的項目類型。 第二個參數指定的陣列維度 （預設值是 1，因此只有多維度需要第二個引數）。 陣列物件本身是追蹤控制代碼，且因此必須有 hat。 如果項目型別也是參考型別，它還需要 hat。 例如，上述範例中，當新的語法中，以表示如下所示：

```
void PrintValues( array<Object^>^ myArr );
void PrintValues( array<int,3>^ myArr );
```

因為參考類型的追蹤控制代碼，而不是物件，就可以指定 CLR 陣列的函式的傳回型別。 （相反地，它不能指定原生陣列函式的傳回型別）。這麼做的 Managed Extensions 的語法是有點非直覺式的。 例如: 

```
Int32 f() [];
int GetArray() __gc[];
```

Visual c + + 中，宣告是更簡單。 例如，套用至物件的

```
array<Int32>^ f();
array<int>^ GetArray();
```

語言的這兩個版本都支援在本機的 managed 陣列的速記初始化。 例如: 

```
int GetArray() __gc[] {
   int a1 __gc[] = { 1, 2, 3, 4, 5 };
   Object* myObjArray __gc[] = {
      __box(26), __box(27), __box(28), __box(29), __box(30)
   };
   return a1;
}
```

已簡化許多新語法中 (請注意，因為 boxing 是隱含在新語法中，`__box`運算子已消除-請參閱[實值類型和其行為 (C + + /cli CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)討論):

```
array<int>^ GetArray() {
   array<int>^ a1 = {1,2,3,4,5};
   array<Object^>^ myObjArray = {26,27,28,29,30};
   return a1;
}
```

因為陣列是 CLR 參考類型，每個陣列物件的宣告會是追蹤控制代碼。 因此，必須在 CLR 堆積配置陣列物件。 （縮寫標記法隱藏 managed 的堆積配置）。以下是在 Managed Extensions 的陣列物件初始化的明確形式：

```
Object* myArray[] = new Object*[2];
String* myMat[,] = new String*[4,4];
```

在新語法中，`new`會取代運算式`gcnew`。 維度的大小會作為參數傳遞至`gcnew`運算式，如下所示：

```
array<Object^>^ myArray = gcnew array<Object^>(2);
array<String^,2>^ myMat = gcnew array<String^,2>(4,4);
```

在新語法中，可以遵循明確的初始設定清單`gcnew`運算式; 這不支援在 Managed Extensions 中。 例如: 

```
// explicit initialization list following gcnew
// was not supported in Managed Extensions
array<Object^>^ myArray =
   gcnew array<Object^>(4){ 1, 1, 2, 3 };
```

## <a name="see-also"></a>另請參閱

[Managed 類型 (C + + /cli CL)](../dotnet/managed-types-cpp-cl.md)<br/>
[陣列](../windows/arrays-cpp-component-extensions.md)
---
title: 變更為轉換運算子 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- conversion operators
- operators [C++], explicit type conversion
- type conversion, explicit conversions
- conversions, explicit
- explicit keyword [C++]
ms.assetid: 9b83925c-71b7-4bd3-ac2e-843dd7c7f184
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 03b17c5abc559289a9f85a10b9c5914b49498922
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46381103"
---
# <a name="changes-to-conversion-operators"></a>轉換運算子的變更

轉換運算子的語法已從 Managed Extensions for c + + Visual c + +。

其中一個範例是撰寫`op_Implicit`指定轉換。 以下是定義`MyDouble`取自語言規格：

```
__gc struct MyDouble {
   static MyDouble* op_Implicit( int i );
   static int op_Explicit( MyDouble* val );
   static String* op_Explicit( MyDouble* val );
};
```

這表示指定的整數，轉換成整數的演算法`MyDouble`係由`op_Implicit`運算子。 此外，將會以隱含方式執行該轉換編譯器。 同樣地，給予`MyDouble`物件，這兩個`op_Explicit`運算子所提供的個別演算法將該物件轉換成整數或 managed`String`實體。 不過，編譯器不會執行轉換，除非使用者明確要求。

在 C# 中，這看起來像這樣：

```
class MyDouble {
   public static implicit operator MyDouble( int i );
   public static explicit operator int( MyDouble val );
   public static explicit operator string( MyDouble val );
};
```

C# 程式碼看起來更像 c + + Managed Extensions for c + + 一樣。 不在新語法中的案例。

ISO c + + 委員會導入關鍵字`explicit`，以降低非預期的結果集，例如`Array`類別可接受單一整數引數，因為維度會隱含地轉換成任何整數`Array`物件的是不是您想要的功能相同。 若要避免這個問題的方法之一是虛擬的第二個引數的建構函式的一個設計慣例

相反地，您不應該提供一組轉換設計 c + + 類別型別時。 最好的範例，是標準字串類別。 隱含轉換為的單一引數建構函式的 C 樣式字串。 不過，它不提供對應的隱含轉換運算子-，將字串轉換的物件為 C 樣式字串，但是會要求使用者明確叫用具名函式-在此情況下， `c_str()`。

因此，建立關聯的轉換運算子 （和做為封裝轉換成單一的宣告形式的集合） 的隱含/明確行為似乎是改善原始 c + + 支援的轉換運算子，最終導致`explicit`關鍵字。 轉換運算子的 Visual c + + 語言支援看起來像這樣，這是由於運算子支援隱含的應用程式的轉換演算法的預設行為比 C# 的：

```
ref struct MyDouble {
public:
   static operator MyDouble^ ( int i );
   static explicit operator int ( MyDouble^ val );
   static explicit operator String^ ( MyDouble^ val );
};
```

另一項變更是，單一引數的建構函式會被視為它被宣告為`explicit`。 這表示，以觸發其引動過程，則需要明確轉換。 不過請注意，是否定義明確轉換運算子，它並沒有單一引數建構函式，會叫用。

## <a name="see-also"></a>另請參閱

[在類別或介面中的成員宣告 (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)
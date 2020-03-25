---
title: 繼承關鍵字
ms.date: 11/04/2016
f1_keywords:
- __multiple_inheritance
- __single_inheritance_cpp
- __virtual_inheritance_cpp
- __virtual_inheritance
- __multiple_inheritance_cpp
- __single_inheritance
helpviewer_keywords:
- __single_inheritance keyword [C++]
- declaring derived classes [C++]
- keywords [C++], inheritance keywords
- __multiple_inheritance keyword [C++]
- __virtual_inheritance keyword [C++]
- inheritance, declaring derived classes
- derived classes [C++], declaring
- inheritance, keywords
ms.assetid: bb810f56-7720-4fea-b8b6-9499edd141df
ms.openlocfilehash: 781673582cb2c3086677b05abc6a7eb73eeabdb4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178173"
---
# <a name="inheritance-keywords"></a>繼承關鍵字

**Microsoft 專屬**

```
class [__single_inheritance] class-name;
class [__multiple_inheritance] class-name;
class [__virtual_inheritance] class-name;
```

其中：

*類別名稱*<br/>
所要宣告類別的名稱。

C++ 可讓您在定義類別之前宣告類別成員的指標。 例如：

```cpp
class S;
int S::*p;
```

在上述程式碼中，`p` 宣告為類別 S 的整數成員指標。不過，此程式碼尚未定義 `class S`;它只會宣告。 當編譯器遇到這類指標時，必須將指標的表示法一般化。 表示法的大小取決於指定的繼承模型。 有四種方式可將繼承模型指定至編譯器：

- 在 IDE 的 [**成員指標標記法**] 底下

- 在命令列中使用[/vmg](../build/reference/vmb-vmg-representation-method.md)參數

- 使用[pointers_to_members](../preprocessor/pointers-to-members.md) pragma

- 使用繼承關鍵字 **__single_inheritance**、 **__multiple_inheritance**和 **__virtual_inheritance**。 這項技術能夠以每個類別為基礎控制繼承模型。

    > [!NOTE]
    >  如果您總是在定義類別之後宣告類別成員的指標，就不需要使用上述任何選項。

在類別定義之前宣告類別成員的指標，會影響所產生可執行檔的大小和速度。 類別使用的繼承越複雜，用來表示類別成員指標所需的位元組數目就越多，而且用來解譯指標的程式碼也會越大。 單一繼承最不複雜，而虛擬繼承最為複雜。

如果上述範例變更為：

```cpp
class __single_inheritance S;
int S::*p;
```

無論命令列選項或 pragma 為何，`class S` 成員的指標都會盡可能使用最小的表示法。

> [!NOTE]
>  類別成員指標表示法的同一個向前宣告應出現在宣告該類別成員指標的每一個轉譯單位中，而且宣告應在成員指標宣告之前發生。

為了與舊版相容，除非指定了編譯器選項[/za __Multiple_inheritance 停用語言擴充功能）](../build/reference/za-ze-disable-language-extensions.md) ，否則 **_single_inheritance**、 **_multiple_inheritance**和 **_virtual_inheritance**都是 **__single_inheritance**、 **__virtual_inheritance**和 **\(** 的同義字。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)

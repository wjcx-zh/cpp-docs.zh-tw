---
title: 編譯器警告 (層級 1) C4691
ms.date: 11/04/2016
f1_keywords:
- C4691
helpviewer_keywords:
- C4691
ms.assetid: 722133d9-87f6-46c1-9e86-9825453d6999
ms.openlocfilehash: 6a4d1de621983794acfae4de7707ba127df9a1b7
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90685563"
---
# <a name="compiler-warning-level-1-c4691"></a>編譯器警告 (層級 1) C4691

' type '：參考的型別必須在未參考的元件 ' file ' 中，而是以目前的轉譯單位定義的類型

未參考包含原始類型定義的中繼資料檔案，且編譯器使用區欄位型別定義。

在您 *要重建檔案的情況下，* 可以使用 pragma [警告](../../preprocessor/warning.md)來忽略或關閉 C4691。  也就是說，如果您要建立的檔案與編譯器預期尋找類型定義的檔案相同，您可以忽略 C4691。

但是，如果編譯器使用的定義不是來自中繼資料所參考的相同元件，則可能會發生未預期的行為;CLR 型別不僅以型別的名稱，也是由元件所輸入。  也就是說，來自元件 z.dll 的類型 Z 與元件 y.dll 的類型 Z 不同。

## <a name="examples"></a>範例

此範例包含原始的型別定義。

```cpp
// C4691_a.cpp
// compile with: /clr /LD /W1
public ref class Original_Type {};
```

這個範例參考 C4691_a.dll，並宣告 Original_Type 類型的欄位。

```cpp
// C4691_b.cpp
// compile with: /clr /LD
#using "C4691_a.dll"
public ref class Client {
public:
   Original_Type^ ot;
};
```

下列範例會產生 C4691。  請注意，此範例包含 Original_Type 的定義，而且不會參考 C4691a.dll。

若要解決這個問題，請參考包含原始型別定義的中繼資料檔案，並移除區域宣告和定義。

```cpp
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

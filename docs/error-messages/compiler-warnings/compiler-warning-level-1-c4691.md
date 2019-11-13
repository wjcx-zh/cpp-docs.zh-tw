---
title: 編譯器警告（層級1） C4691
ms.date: 11/04/2016
f1_keywords:
- C4691
helpviewer_keywords:
- C4691
ms.assetid: 722133d9-87f6-46c1-9e86-9825453d6999
ms.openlocfilehash: 6124171bb5f257dac1dd972f7943d001fb54c9ca
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051364"
---
# <a name="compiler-warning-level-1-c4691"></a>編譯器警告（層級1） C4691

' type '：參考的類型必須在未參考的元件 ' file ' 中，但目前的轉譯單位中所定義的類型已改為使用

未參考包含原始類型定義的中繼資料檔案，而且編譯器會使用區欄位型別定義。

如果您*要重建檔案*，可以忽略或關閉 C4691，並使用 pragma [warning](../../preprocessor/warning.md)。  也就是說，如果您要建立的檔案與編譯器預期用來尋找類型定義的檔案相同，您可以忽略 C4691。

不過，如果編譯器使用的定義不是中繼資料中所參考的相同元件，則可能會發生非預期的行為;CLR 型別不只會以類型的名稱，也會由元件來輸入。  也就是，從元件 z 的類型 Z 與元件 y .dll 的類型 Z 不同。

## <a name="example"></a>範例

這個範例包含原始型別定義。

```cpp
// C4691_a.cpp
// compile with: /clr /LD /W1
public ref class Original_Type {};
```

## <a name="example"></a>範例

這個範例會參考 C4691_a .dll，並宣告 Original_Type 類型的欄位。

```cpp
// C4691_b.cpp
// compile with: /clr /LD
#using "C4691_a.dll"
public ref class Client {
public:
   Original_Type^ ot;
};
```

## <a name="example"></a>範例

下列範例會產生 C4691。  請注意，此範例包含 Original_Type 的定義，而且不會參考 C4691a。

若要解決此問題，請參考包含原始類型定義的中繼資料檔案，並移除本機宣告和定義。

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
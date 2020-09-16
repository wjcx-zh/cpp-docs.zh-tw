---
title: 連結器工具錯誤 LNK2022
ms.date: 11/04/2016
f1_keywords:
- LNK2022
helpviewer_keywords:
- LNK2022
ms.assetid: d2128c73-dde3-4b8e-a9b2-0a153acefb3b
ms.openlocfilehash: 187a63cb4bd22fc5e0d35523d97f438ba56b8576
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686354"
---
# <a name="linker-tools-error-lnk2022"></a>連結器工具錯誤 LNK2022

> 中繼資料作業失敗 (*HRESULT*) ： *error_message*

連結器在合併中繼資料時偵測到錯誤。 中繼資料錯誤必須解決才能成功連結。

診斷此問題的其中一種方式是在物件檔案上執行 **ildasm 權杖** ，以找出哪些類型具有中列出的權杖 `error_message` ，並尋找差異。  在中繼資料中，相同名稱的兩個不同類型無效，即使只有 LayoutType 屬性不同也是一樣。

LNK2022 的其中一個原因是，類型 (（例如結構) 存在於具有相同名稱的多個 compilands 中，但有衝突的定義，以及當您使用 [/clr](../../build/reference/clr-common-language-runtime-compilation.md)進行編譯時。  在此情況下，請確定類型在所有 compilands 中都具有相同的定義。  類型名稱列在中 `error_message` 。

LNK2022 的另一個可能原因是當連結器在不同的位置找到中繼資料檔案，而該檔案與編譯器 (的 [#using](../../preprocessor/hash-using-directive-cpp.md) ) 不同。 確保中繼資料檔 (.dll 或 .netmodule) 所在位置是與傳遞給連結器時相同，也與傳遞給編譯器時相同。

建立 ATL 應用程式時， `_ATL_MIXED` 所有 compilands 都必須使用宏，如果至少有一個使用的話。

## <a name="examples"></a>範例

下列範例會定義空的型別。

```cpp
// LNK2022_a.cpp
// compile with: /clr /c
public ref class Test {};
```

此範例顯示您無法連結兩個原始程式碼檔案，其中包含相同名稱但不同定義的類型。

下列範例會產生 LNK2022。

```cpp
// LNK2022_b.cpp
// compile with: LNK2022_a.cpp /clr /LD
// LNK2022 expected
public ref class Test {
   void func() {}
   int var;
};
```

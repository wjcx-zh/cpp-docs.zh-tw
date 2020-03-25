---
title: 連結器工具錯誤 LNK2022
ms.date: 11/04/2016
f1_keywords:
- LNK2022
helpviewer_keywords:
- LNK2022
ms.assetid: d2128c73-dde3-4b8e-a9b2-0a153acefb3b
ms.openlocfilehash: d30dad6f8ad146ff467eb4eaf32b21dd6950d25f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194638"
---
# <a name="linker-tools-error-lnk2022"></a>連結器工具錯誤 LNK2022

> 中繼資料作業失敗（*HRESULT*）： *error_message*

連結器在合併中繼資料時偵測到錯誤。 必須解析中繼資料錯誤，才能成功連結。

診斷此問題的其中一種方法是在物件檔案上執行**ildasm** token，以尋找哪些類型具有 `error_message`中列出的權杖，並尋找差異。  在中繼資料中，兩個具有相同名稱的不同類型是不正確，即使 LayoutType 屬性不同也一樣。

LNK2022 的其中一個原因是當類型（例如結構）存在於具有相同名稱的多個 compilands 中，但具有衝突的定義，以及當您使用[/clr](../../build/reference/clr-common-language-runtime-compilation.md)進行編譯時。  在此情況下，請確定類型在所有 compilands 中都有相同的定義。  類型名稱列在 `error_message`中。

另一個可能的 LNK2022 原因是當連結器在指定給編譯器的不同位置（使用[#using](../../preprocessor/hash-using-directive-cpp.md) ）找到中繼資料檔案。 確保中繼資料檔 (.dll 或 .netmodule) 所在位置是與傳遞給連結器時相同，也與傳遞給編譯器時相同。

在建立 ATL 應用程式時，所有 compilands 都需要使用宏 `_ATL_MIXED` （如果至少在一個中使用的話）。

## <a name="example"></a>範例

下列範例會定義空的型別。

```cpp
// LNK2022_a.cpp
// compile with: /clr /c
public ref class Test {};
```

## <a name="example"></a>範例

這個範例顯示您無法連結兩個原始程式碼檔，其中包含名稱相同但定義不同的類型。

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

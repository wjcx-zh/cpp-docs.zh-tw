---
title: 連結器工具錯誤 LNK2022
ms.date: 11/04/2016
f1_keywords:
- LNK2022
helpviewer_keywords:
- LNK2022
ms.assetid: d2128c73-dde3-4b8e-a9b2-0a153acefb3b
ms.openlocfilehash: e55202274c5ec3982f784ad6cdf074a5a99e922f
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345340"
---
# <a name="linker-tools-error-lnk2022"></a>連結器工具錯誤 LNK2022

> 中繼資料作業失敗 (*HRESULT*): *error_message*

連結器偵測到合併中繼資料時的錯誤。 中繼資料必須先解決錯誤連結成功。

若要診斷此問題的一個方式是執行**ildasm-語彙基元**上尋找有哪些類型的物件檔案的語彙基元列`error_message`，並尋找差異。  中繼資料，具有相同名稱的兩種不同類型不正確，即使只是 LayoutType 屬性不同。

其中一個原因 LNK2022 是時 （例如結構） 的型別存在於多個編譯單位名稱相同，但含有衝突的定義，以及當您使用編譯[/clr](../../build/reference/clr-common-language-runtime-compilation.md)。  在此情況下，請確定該類型具有相同的定義，在所有編譯中。  類型名稱會列在`error_message`。

連結器會尋找在不同位置的中繼資料檔案於指定給編譯器時，另一個可能的原因如 LNK2022 (與[#using](../../preprocessor/hash-using-directive-cpp.md) )。 確保中繼資料檔 (.dll 或 .netmodule) 所在位置是與傳遞給連結器時相同，也與傳遞給編譯器時相同。

建置 ATL 應用程式，使用巨集時`_ATL_MIXED`需要在所有編譯中，如果它用在至少一個。

## <a name="example"></a>範例

下列範例會定義空的型別。

```cpp
// LNK2022_a.cpp
// compile with: /clr /c
public ref class Test {};
```

## <a name="example"></a>範例

此範例示範您無法連結兩個來源的程式碼檔案包含類型的相同名稱但不同的定義。

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
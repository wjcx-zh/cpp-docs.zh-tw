---
title: noreturn
ms.date: 11/04/2016
f1_keywords:
- noreturn_cpp
helpviewer_keywords:
- __declspec keyword [C++], noreturn
- noreturn __declspec keyword
ms.assetid: 9c6517e5-22d7-4051-9974-3d2200ae4d1d
ms.openlocfilehash: f9ca61c9d734ccdd6b8d8374ed3a7c4128ee3d5e
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857368"
---
# <a name="noreturn"></a>noreturn

**Microsoft 專屬**

這個 **__declspec**屬性會告知編譯器，函數不會傳回。 因此，編譯器知道呼叫 **__declspec （noreturn）** 函數之後的程式碼無法連線。

如果編譯器發現某個函式包含的控制路徑不會傳回值，則會產生警告 (C4715) 或錯誤訊息 (C2202)。 如果因為函式永遠不會傳回而無法到達控制路徑，您可以使用 **__declspec （noreturn）** 來避免這個警告或錯誤。

> [!NOTE]
>  將 **__declspec （noreturn）** 新增至預期會傳回的函式可能會導致未定義的行為。

## <a name="example"></a>範例

在下列範例中， **else**子句不包含 return 語句。  將 `fatal` 宣告為 **__declspec （noreturn）** 會避免出現錯誤或警告訊息。

```cpp
// noreturn2.cpp
__declspec(noreturn) extern void fatal () {}

int main() {
   if(1)
     return 1;
   else if(0)
     return 0;
   else
     fatal();
}
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>請參閱

[__declspec](../cpp/declspec.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)
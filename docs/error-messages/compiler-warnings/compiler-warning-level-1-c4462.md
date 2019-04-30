---
title: 編譯器警告 (層級 1) C4462
ms.date: 10/25/2017
f1_keywords:
- C4462
helpviewer_keywords:
- C4462
ms.assetid: 4e20aca4-293e-4c75-a83d-961c27ab7840
ms.openlocfilehash: bd4d5c1fd7dd8d7419fc901149ceab7e769e7076
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404048"
---
# <a name="compiler-warning-level-1-c4462"></a>編譯器警告 (層級 1) C4462

> 無法判斷類型的 GUID。 程式可能在執行階段失敗。

警告 C4462 當公用 `TypedEventHandler` 的其中一個型別參數做為封入類別的參考時，Windows 執行階段應用程式或元件中就會發生警告 C4462。

這個警告會自動升級為錯誤。 如果您想要修改此行為，使用[#pragma 警告](../../preprocessor/warning.md)。 比方說，若要讓 C4462 層級 4 警告問題，這行加入您的原始程式碼檔：

```cpp
#pragma warning(4:4462)
```

## <a name="example"></a>範例

此範例會產生警告 C4462:

```cpp
namespace N
{
    public ref struct EventArgs sealed {};
    public ref struct R sealed
    {
        R() {}
        event Windows::Foundation::TypedEventHandler<R ^, EventArgs^>^ e;
    };
}

[Platform::MTAThread]
int main()
{
    auto x = ref new N::R();
}
```

有兩種方式可以解決此錯誤。 一種方式是指定事件內部存取範圍，讓相同可執行檔中的程式碼可以使用，但不對其他 Windows 執行階段元件中的程式碼提供，如下一個範例中所示。

```cpp
internal:
    event Windows::Foundation::TypedEventHandler<R ^, EventArgs^>^ e;
```

如果事件必須為公用，則您可以使用另一種解決方法，也就是透過預設介面將它公開：

```cpp
ref struct R;
public interface struct IR{ event Windows::Foundation::TypedEventHandler<R ^, EventArgs^>^ e;};

public ref struct R sealed : [Windows::Foundation::Metadata::Default] IR
{
    R() {}
    virtual event Windows::Foundation::TypedEventHandler<R ^, EventArgs^>^ e;
};
```

只有在從另一個元件存取 `Windows::Foundation::TypedEventHandler<R^, EventArgs^>^` 類型時，才會使用該類型的 GUID。 第一個解決方法有效，是因為解決後只能從它自己的元件內存取。 否則，編譯器必須假設最糟情況並發出警告。

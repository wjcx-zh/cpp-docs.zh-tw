---
title: 平台、預設和 CLI 命名空間  (C++/CLI 和 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- lang
- cli
helpviewer_keywords:
- lang namespace
- cli namespace
ms.assetid: 9d38bd1e-dc78-47d1-a84b-9b4683e52c9c
ms.openlocfilehash: aedb8b7954eaa4bb1cf1060725103cd725c3f180
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181820"
---
# <a name="platform-default-and-cli-namespaces--ccli-and-ccx"></a>平台、預設和 CLI 命名空間  (C++/CLI 和 C++/CX)

命名空間會限定語言項目的名稱，因此名稱不會與原始程式碼中其他位置的相同名稱發生衝突。 例如，名稱衝突可能會使編譯器無法辨識[即時線上關鍵字](context-sensitive-keywords-cpp-component-extensions.md)。 編譯器會使用命名空間，但是命名空間不會保留在編譯的組件中。

## <a name="all-runtimes"></a>所有執行階段

當您建立專案時，Visual Studio 會為專案提供一個預設的命名空間。 雖然在 C++/CX 中，.winmd 檔案的名稱必須與根命名空間的名稱相符，不過您可以手動將命名空間重新命名。

## <a name="windows-runtime"></a>Windows 執行階段

如需詳細資訊，請參閱[命名空間和類型可視性 (C++/CX)](../cppcx/namespaces-and-type-visibility-c-cx.md)。

### <a name="requirements"></a>需求

編譯器選項：`/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="syntax"></a>語法

```cpp
using namespace cli;
```

### <a name="remarks"></a>備註

C++/CLI 支援 **cli** 命名空間。 使用 `/clr` 進行編譯時，會隱含＜語法＞一節中的 **using** 陳述式。

**cli** 命名空間中具有下列語言功能：

- [陣列](arrays-cpp-component-extensions.md)

- [interior_ptr (C++/CLI)](interior-ptr-cpp-cli.md)

- [pin_ptr (C++/CLI)](pin-ptr-cpp-cli.md)

- [safe_cast](safe-cast-cpp-component-extensions.md)

### <a name="requirements"></a>需求

編譯器選項：`/clr`

### <a name="examples"></a>範例

以下程式碼範例會示範可以在 **cli** 命名空間中使用符號做為程式碼中的使用者定義符號。  不過，一旦這麼做，就必須明確或隱含地限定對同名 **cli** 語言項目的參考。

```cpp
// cli_namespace.cpp
// compile with: /clr
using namespace cli;
int main() {
   array<int> ^ MyArray = gcnew array<int>(100);
   int array = 0;

   array<int> ^ MyArray2 = gcnew array<int>(100);   // C2062

   // OK
   cli::array<int> ^ MyArray2 = gcnew cli::array<int>(100);
   ::array<int> ^ MyArray3 = gcnew ::array<int>(100);
}
```

## <a name="see-also"></a>另請參閱

[適用於.NET 和 UWP 的元件延伸模組](component-extensions-for-runtime-platforms.md)
